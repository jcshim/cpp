```
#include <opencv2/opencv.hpp>
#include <opencv2/dnn.hpp>
#include <iostream>
using namespace cv;
using namespace dnn;
using namespace std;

int main() {
    // 모델 로드 (ONNX 또는 Caffe 등)
    Net net = readNetFromONNX("d:/mnist-12.onnx");

    // 입력 이미지 로드 (예: 숫자 5 이미지)
    Mat img = imread("d:/8.png", IMREAD_GRAYSCALE); // 흑백 이미지

    // 전처리: 28x28 리사이즈, float 변환, 정규화
    resize(img, img, Size(28, 28));
    img.convertTo(img, CV_32F, 1.0 / 255);  // 0~1로 정규화
    Mat blob = blobFromImage(img);          // (1, 1, 28, 28)

    // 모델 입력 및 추론
    net.setInput(blob);
    Mat output = net.forward();

    // 결과 해석
    Point classId;
    double confidence;
    minMaxLoc(output, 0, &confidence, 0, &classId);
    cout << "예측된 숫자: " << classId.x << " (신뢰도: " << confidence << ")" << endl;

    return 0;
}
```

좋습니다! 아래는 **Visual Studio에서 NuGet으로 OpenCV 4.2를 설치**하고,  
**ONNX 모델(`mnist-8.onnx`)과 28x28 숫자 이미지(`8.png`)**를 사용하여 숫자를 인식하는  
**C++ 전용 초보자용 매뉴얼**입니다.

---

# 🧠 C++ 초보자를 위한 숫자 인식 실습 매뉴얼  
(Visual Studio + OpenCV 4.2 + ONNX 모델)

---

## ✅ 준비물 요약

| 항목         | 설명 |
|--------------|------|
| Visual Studio | 2022 이상 권장 |
| OpenCV       | NuGet으로 `opencv.windows` 설치 |
| ONNX 모델   | `mnist-8.onnx` ([다운로드 링크](https://github.com/onnx/models/raw/main/vision/classification/mnist/model/mnist-8.onnx)) |
| 테스트 이미지 | 28x28 흑백 PNG, 이름은 `8.png` |

---

## ✅ 1단계: Visual Studio C++ 프로젝트 만들기

1. **Visual Studio 실행**
2. [새 프로젝트] > `빈 콘솔 앱(C++)` 선택
3. 프로젝트 이름: `My`
4. [빈 프로젝트] 체크 > 생성

---

## ✅ 2단계: NuGet으로 OpenCV 설치

1. 솔루션 탐색기 > 프로젝트 우클릭 > `NuGet 패키지 관리`
2. [찾아보기] 탭에서 `opencv4.2` 검색 후 설치

---

## ✅ 3단계: 모델 & 이미지 파일 준비

### 🔹 mnist-8.onnx 다운로드
- 주소:  
  [https://github.com/onnx/models/raw/main/vision/classification/mnist/model/mnist-8.onnx](https://github.com/onnx/models/raw/main/vision/classification/mnist/model/mnist-8.onnx)

- 파일명을 `mnist-8.onnx`로 유지  
- **경로 예시**: `D:\mnist-8.onnx`

### 🔹 8.png 이미지 준비 (28x28 픽셀, 흑백)
프람프트: 필기체 숫자 8 만들어줘

---

## ✅ 4단계: C++ 전체 코드 작성 (`main.cpp`)

```cpp
#include <opencv2/opencv.hpp>
#include <opencv2/dnn.hpp>
#include <iostream>

using namespace cv;
using namespace dnn;
using namespace std;

int main() {
    // 모델 경로 설정 (자신의 경로로 수정)
    string modelPath = "D:/mnist-8.onnx";
    string imagePath = "D:/8.png";

    // 모델 로드
    Net net = readNetFromONNX(modelPath);

    // 이미지 로드
    Mat img = imread(imagePath, IMREAD_GRAYSCALE);
    if (img.empty()) {
        cerr << "이미지를 불러올 수 없습니다: " << imagePath << endl;
        return -1;
    }

    // 전처리: 28x28, float32, 0~1 정규화
    resize(img, img, Size(28, 28));
    img.convertTo(img, CV_32F, 1.0 / 255);
    Mat blob = blobFromImage(img);  // (1, 1, 28, 28)

    // 추론
    net.setInput(blob);
    Mat output = net.forward();  // (1, 10)

    // 결과 출력
    Point classId;
    double confidence;
    minMaxLoc(output, 0, &confidence, 0, &classId);
    cout << "예측된 숫자: " << classId.x << " (신뢰도: " << confidence << ")" << endl;

    return 0;
}
```

## ✅ 5단계: 실행 결과

성공적으로 실행되면 다음과 같은 결과가 나옵니다:

```
예측된 숫자: 8 (신뢰도: 0.9983)
```

---

## ✅ 문제 해결 FAQ

| 증상 | 해결 방법 |
|------|-----------|
| 이미지가 안 열림 | 경로 및 파일 형식(PNG) 확인 |
| 모델 오류 | `mnist-8.onnx` 위치 및 이름 확인 |
| DLL 오류 | DLL을 실행 디렉토리에 복사 |
| 링커 오류 | `.lib` 파일 추가, 경로 지정 확인 |
