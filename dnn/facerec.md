아래는 **C++과 OpenCV를 처음 접하는 완전 초보자**도 이해할 수 있도록 이 얼굴 인식 프로그램을 단계별로 쉽게 설명한 설명서입니다. 이 코드는 등록된 얼굴과 테스트 이미지를 비교해 **누구인지 자동으로 인식**해주는 예제입니다.

---

## 💡 이 프로그램이 하는 일 한 줄 요약

📷 얼굴 사진을 보고 → 🤖 등록된 얼굴들과 비교해서 → 🧑 누구인지 알려줍니다!

---

## 1. 필요한 준비물

### 📁 필수 파일

* 얼굴 검출용 Caffe 모델 2개

  * `deploy.prototxt`
  * `res10_300x300_ssd_iter_140000.caffemodel`
* 얼굴 인식용 ONNX 모델

  * `face_recognition_sface_2021dec.onnx`
* 비교할 사람 사진 (예: `ko.jpg`, `shim.jpg`)
* 테스트할 사진 (예: `shim1.jpg`)

### 🧰 사용 라이브러리

* OpenCV (`opencv_core`, `opencv_imgproc`, `opencv_dnn`, `opencv_highgui`, `opencv_imgcodecs`)
* C++ STL (`iostream`, `map` 등)

---

## 2. 코드 설명

### 🚀 시작: 필요한 라이브러리 불러오기

```cpp
#include <opencv2/opencv.hpp>
#include <opencv2/dnn.hpp>
#include <iostream>
#include <map>
```

OpenCV는 이미지 처리, DNN은 딥러닝 모델을 불러올 때 사용됩니다.

---

### 📏 함수 1: 코사인 유사도 계산

```cpp
float cosineSimilarity(const Mat& a, const Mat& b) {
    return a.dot(b) / (norm(a) * norm(b));
}
```

두 얼굴이 얼마나 비슷한지를 수치로 계산합니다. 1에 가까울수록 유사합니다.

---

### 🧠 함수 2: 얼굴 특징 추출

```cpp
Mat extractFeature(Net& recognizer, const Mat& face)
```

얼굴 이미지를 넣으면 **128차원 특징 벡터**를 반환합니다. 이 벡터로 사람을 구별합니다.

---

### 📌 main() 함수 시작

#### 🧱 얼굴 인식 모델 불러오기

```cpp
dnn::Net detector = readNetFromCaffe(...);
dnn::Net recognizer = readNetFromONNX(...);
```

* `detector`: 얼굴이 어디 있는지 찾는 모델
* `recognizer`: 그 얼굴이 누구인지 확인하는 모델

---

### 🗂️ 얼굴 등록 (DB 만들기)

```cpp
map<string, Mat> faceDB;
```

이름과 특징 벡터를 짝지어 저장합니다.

```cpp
{"Ko", "d:/ko.jpg"}, {"Shim", "d:/shim.jpg"}
```

* 이 사람들의 얼굴을 분석해서 `faceDB["Ko"]`, `faceDB["Shim"]`에 저장합니다.

---

### 🕵️ 테스트 이미지에서 얼굴 찾기

```cpp
Mat testImg = imread("d:/shim1.jpg");
```

* 얼굴을 검출하고, 특징을 추출합니다.

---

### ⚖️ 등록된 얼굴과 비교

```cpp
float sim = cosineSimilarity(testFeature, regFeature);
```

* 등록된 사람들과 유사도를 비교합니다.
* 유사도가 0.6 이상인 사람을 "일치!"라고 판단합니다.

---

### 🎯 결과 출력

```cpp
rectangle(), putText(), imshow()
```

* 얼굴 주변에 초록색 박스를 그립니다.
* 이름을 얼굴 위에 표시합니다.
* `d:/result.jpg`로 저장합니다.

---

## 3. 실행 순서 요약 (한눈에!)

| 단계 | 설명                    |
| -- | --------------------- |
| 1  | 등록할 얼굴 이미지에서 얼굴 위치 찾기 |
| 2  | 얼굴을 잘라내고 특징 벡터 추출     |
| 3  | 이름과 함께 `map`에 저장      |
| 4  | 테스트 이미지에서 얼굴 찾기       |
| 5  | 등록된 얼굴과 유사도 비교        |
| 6  | 가장 유사한 사람 이름 표시       |
| 7  | 화면에 보여주고, 결과 저장       |

---

## 4. 초보자를 위한 추가 팁

* ❗ 모든 경로는 **절대 경로**로 지정되어 있어야 합니다 (`d:/`).
* 📸 등록 이미지와 테스트 이미지는 **정면 얼굴**일수록 정확도가 높습니다.
* 🤖 모델 다운로드는 직접 해야 하며, 파일명은 변경하지 마세요.
* 🧪 OpenCV는 설치 후 `opencv_world4xxx.dll`이 필요한 경우가 많습니다.

---

## 5. 출력 예시 (결과 화면)

```plaintext
[초록색 박스] + [Ko]
또는
[초록색 박스] + [Unknown]
```

```
# [소스코드](https://cafe.naver.com/cpp1/171)
