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
Mat extractFeature(cv::dnn::Net& recognizer, const Mat& face) {
    Mat blob = dnn::blobFromImage(face, 1.0 / 255.0, Size(112, 112), Scalar(), true, false);
    recognizer.setInput(blob);
    return recognizer.forward().clone();  // clone() 추가로 안전하게 사용
}

int main() {
    // 얼굴 검출 모델 로드 (Caffe)
    dnn::Net detector = 
    dnn::readNetFromCaffe("d:/deploy.prototxt", "d:/res10_300x300_ssd_iter_140000.caffemodel");

    if (detector.empty()) {
        cerr << "Error loading detector model!" << endl;
        return -1;
    }

    // 얼굴 인식 모델 로드 (ONNX)
    dnn::Net recognizer = dnn::readNetFromONNX("d:/face_recognition_sface_2021dec.onnx");
    if (recognizer.empty()) {
        cerr << "Error loading recognizer model!" << endl;
        return -1;
    }

    // 1. 등록 얼굴 DB (이름 → 특징 벡터)
    map<string, Mat> faceDB;
    vector<pair<string, string>> registration = {
        {"Ko", "d:/ko.jpg"},
        {"Shim", "d:/shim.jpg"}
    };

    for (auto& [name, imgPath] : registration) {
        Mat img = imread(imgPath);
        if (img.empty()) {
            cerr << "Could not load: " << imgPath << endl;
            continue;
        }

        // 얼굴 검출
        Mat blob = dnn::blobFromImage(img, 1.0, Size(300, 300), Scalar(104, 177, 123));
        detector.setInput(blob);
        Mat detections = detector.forward();
        Mat detMat(detections.size[2], detections.size[3], CV_32F, detections.ptr<float>());

        for (int i = 0; i < detMat.rows; ++i) {
            float confidence = detMat.at<float>(i, 2);
            if (confidence > 0.5f) {
                int x1 = static_cast<int>(detMat.at<float>(i, 3) * img.cols);
                int y1 = static_cast<int>(detMat.at<float>(i, 4) * img.rows);
                int x2 = static_cast<int>(detMat.at<float>(i, 5) * img.cols);
                int y2 = static_cast<int>(detMat.at<float>(i, 6) * img.rows);
                Rect faceRect(Point(x1, y1), Point(x2, y2));
                Mat face = img(faceRect).clone();

                faceDB[name] = extractFeature(recognizer, face);
                break;
            }
        }
    }

    // 2. 테스트 이미지 로딩
    Mat testImg = imread("d:/shim1.jpg");  // 경로 수정
    if (testImg.empty()) {
        cerr << "Failed to load test image!" << endl;
        return -1;
    }

    // 얼굴 검출
    Mat blob = dnn::blobFromImage(testImg, 1.0, Size(300, 300), Scalar(104, 177, 123));
    detector.setInput(blob);
    Mat detections = detector.forward();
    Mat detMat(detections.size[2], detections.size[3], CV_32F, detections.ptr<float>());

    for (int i = 0; i < detMat.rows; ++i) {
        float confidence = detMat.at<float>(i, 2);
        if (confidence > 0.5f) {
            int x1 = static_cast<int>(detMat.at<float>(i, 3) * testImg.cols);
            int y1 = static_cast<int>(detMat.at<float>(i, 4) * testImg.rows);
            int x2 = static_cast<int>(detMat.at<float>(i, 5) * testImg.cols);
            int y2 = static_cast<int>(detMat.at<float>(i, 6) * testImg.rows);
            Rect faceRect(Point(x1, y1), Point(x2, y2));
            Mat face = testImg(faceRect).clone();

            // 특징 추출
            Mat testFeature = extractFeature(recognizer, face);

            // DB와 유사도 비교
            string matched = "Unknown";
            float maxSim = 0.0f;

            for (auto& [name, regFeature] : faceDB) {
                float sim = cosineSimilarity(testFeature, regFeature);
                if (sim > maxSim && sim > 0.6f) {
                    maxSim = sim;
                    matched = name;
                }
            }

            rectangle(testImg, faceRect, Scalar(0, 255, 0), 2);
            putText(testImg, matched, Point(x1, y1 - 10), FONT_HERSHEY_SIMPLEX, 0.9, Scalar(0, 0, 255), 2);
        }
    }

    imshow("Face Recognition", testImg);
    imwrite("d:/result.jpg", testImg);  // 결과 저장도 추가
    waitKey(0);
    return 0;
}
```

---

## 📂 폴더 구성 예시

```
프로젝트/
│
├─ d:/deploy.prototxt
├─ d:/res10_300x300_ssd_iter_140000_fp16.caffemodel
├─ d:/face_recognition_sface_2021dec.onnx
├─ d:/shim.jpg   ← 등록용 이미지
├─ d:/ko.jpg
├─ d:/shim1.jpg    ← 인식 테스트 이미지
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
