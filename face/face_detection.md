# 얼굴추출

## '윈도우 데스크톱 마법사'   Project1
### 데스크톱 애플리케이션(.exe)
### [체크] 빈 프로젝트(E) [확인]
### 메뉴 [프로젝트]>아래 [속성]>링커>고급>진입점: mainCRTStartup [확인]

## 오른쪽 솔루션 탐색기: 
### 소스파일 > 마우스 오른버튼>추가[D]>새항목>
### FileName.cpp을 main.cpp [추가(A)]

## 메뉴 프로젝트(P)>NuGet 패키지 관리> [찾아보기]탭>'penCV4.2'로 검색>오른쪽 [설치] > 1분 대기

```
#include<OpenCV2/openCV.hpp>
using namespace cv;
int main() {
	Mat img = imread("d:/face/shim.jpg");  // 수정하세요.
	imshow("GKNU", img);
	waitKey(0);
}
```


## [우클릭 → 다른 이름으로 저장(UTF8): haarcascades/haarcascade_frontalface_default.xml](https://raw.githubusercontent.com/opencv/opencv/master/data/haarcascades/haarcascade_frontalface_default.xml)

```
#include<OpenCV2/openCV.hpp>
#include<iostream>
using namespace cv;
int main() {
	Mat img = imread("d:/face/shim.jpg"); // 수정하세요.
	CascadeClassifier hc("D:/face/haarcascade_frontalface_default.xml"); // 수정하세요.
	std::vector<Rect> fs;
	hc.detectMultiScale(img, fs);
	for (auto& f : fs) {
		rectangle(img, f, Scalar(255, 0, 0), 2);
	}
	imshow("Faces", img);
	waitKey(0);
}
```
``
