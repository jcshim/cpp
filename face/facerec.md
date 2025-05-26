# 얼굴인식
`res10_300x300_ssd_iter_140000_fp16.caffemodel`로 얼굴 **검출**, 
`face_recognition_sface_2021dec.onnx`로 얼굴 특징 추출(인식)
**등록된 얼굴 DB와 비교하여 인식**하는 전체 예제

---

## 🧠 구현 개요

### 구성 요소

1. 얼굴 검출: `res10_300x300_ssd_iter_140000_fp16.caffemodel`
2. 특징 추출: `face_recognition_sface_2021dec.onnx`
3. 등록된 얼굴 DB: `std::map<string, cv::Mat>` 형태로 저장
4. 비교 방식: **코사인 유사도(cosine similarity)**

---

## ✅ 전체 C++ 코드

```cpp
#include <opencv2/opencv.hpp>
#include <opencv2/dnn.hpp>
#include <iostream>
#include <map>
#include <cmath>

using namespace cv;
using namespace std;

// 코사인 유사도 계산 함수
float cosineSimilarity(const Mat& a, const Mat& b) {
    return a.dot(b) / (norm(a) * norm(b));
}

// 얼굴 특징 추출 함수
Mat extractFeature(Net& recognizer, const Mat& face) {
    Mat blob = dnn::blobFromImage(face, 1.0 / 255.0, Size(112, 112), Scalar(), true, false);
    recognizer.setInput(blob);
    return recognizer.forward();  // (1 x 128)
}

int main() {
    // 모델 로드
    Net detector = dnn::readNetFromCaffe("deploy.prototxt", "res10_300x300_ssd_iter_140000_fp16.caffemodel");
    Net recognizer = dnn::readNetFromONNX("face_recognition_sface_2021dec.onnx");

    // 등록된 얼굴 DB
    map<string, Mat> faceDB;

    // 얼굴 등록 (예: 이미지 파일 2개)
    vector<pair<string, string>> registration = {
        {"Alice", "alice.jpg"},
        {"Bob", "bob.jpg"}
    };

    for (auto& [name, path] : registration) {
        Mat img = imread(path);
        if (img.empty()) continue;

        // 얼굴 검출
        Mat blob = dnn::blobFromImage(img, 1.0, Size(300, 300), Scalar(104, 177, 123));
        detector.setInput(blob);
        Mat detections = detector.forward();
        Mat detMat(detections.size[2], detections.size[3], CV_32F, detections.ptr<float>());

        for (int i = 0; i < detMat.rows; ++i) {
            float confidence = detMat.at<float>(i, 2);
            if (confidence > 0.5) {
                int x1 = int(detMat.at<float>(i, 3) * img.cols);
                int y1 = int(detMat.at<float>(i, 4) * img.rows);
                int x2 = int(detMat.at<float>(i, 5) * img.cols);
                int y2 = int(detMat.at<float>(i, 6) * img.rows);
                Rect faceRect(Point(x1, y1), Point(x2, y2));
                Mat face = img(faceRect).clone();

                faceDB[name] = extractFeature(recognizer, face);
                break;  // 첫 번째 얼굴만 사용
            }
        }
    }

    // 테스트 이미지 로드
    Mat test = imread("test.jpg");
    if (test.empty()) return -1;

    // 얼굴 검출
    Mat testBlob = dnn::blobFromImage(test, 1.0, Size(300, 300), Scalar(104, 177, 123));
    detector.setInput(testBlob);
    Mat testDetections = detector.forward();
    Mat testMat(testDetections.size[2], testDetections.size[3], CV_32F, testDetections.ptr<float>());

    for (int i = 0; i < testMat.rows; ++i) {
        float confidence = testMat.at<float>(i, 2);
        if (confidence > 0.5) {
            int x1 = int(testMat.at<float>(i, 3) * test.cols);
            int y1 = int(testMat.at<float>(i, 4) * test.rows);
            int x2 = int(testMat.at<float>(i, 5) * test.cols);
            int y2 = int(testMat.at<float>(i, 6) * test.rows);
            Rect faceRect(Point(x1, y1), Point(x2, y2));
            rectangle(test, faceRect, Scalar(0, 255, 0), 2);

            Mat face = test(faceRect).clone();
            Mat testFeat = extractFeature(recognizer, face);

            // DB와 유사도 비교
            string matched = "Unknown";
            float maxSim = 0.0;

            for (auto& [name, feat] : faceDB) {
                float sim = cosineSimilarity(testFeat, feat);
                if (sim > maxSim && sim > 0.5) {  // threshold 조정 가능
                    maxSim = sim;
                    matched = name;
                }
            }

            putText(test, matched, Point(x1, y1 - 10), FONT_HERSHEY_SIMPLEX, 1, Scalar(255, 0, 0), 2);
        }
    }

    imshow("Face Recognition", test);
    waitKey(0);
    return 0;
}
```

---

## 📂 폴더 구성 예시

```
프로젝트/
│
├─ deploy.prototxt
├─ res10_300x300_ssd_iter_140000_fp16.caffemodel
├─ face_recognition_sface_2021dec.onnx
├─ alice.jpg   ← 등록용 이미지
├─ bob.jpg
├─ test.jpg    ← 인식 테스트 이미지
```

---

## ✅ 주요 포인트 요약

| 단계    | 설명                                            |
| ----- | --------------------------------------------- |
| 얼굴 등록 | 얼굴을 검출 후 특징 벡터 추출, `faceDB["이름"] = 특징` 형태로 저장 |
| 얼굴 인식 | 테스트 이미지의 얼굴 특징을 DB와 비교하여 가장 유사한 사람을 출력        |
| 비교 방식 | `cosine similarity`로 유사도 측정 (0.5\~0.6 기준값 추천) |
| 확장 가능 | DB를 파일로 저장, 실시간 웹캠 지원, 다수 얼굴 처리 가능            |

---

### 📌 확장 요청 가능 항목

* 실시간 **웹캠 얼굴 인식**
* DB를 **JSON 또는 CSV로 저장/로드**
* UI 표시 (Qt, OpenCV GUI, etc.)

필요하시면 언제든지 알려주세요!
