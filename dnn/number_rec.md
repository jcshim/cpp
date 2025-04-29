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
