Opencv4.2 Nuget설치

```
#include <opencv2/opencv.hpp>

int main()
{
    cv::Mat img = cv::imread("D:/shim.jpeg"); // 이미지 읽기
    if (img.empty())
        return -1; // 파일 못 읽으면 종료

    cv::imshow("Image", img); // 창에 이미지 띄우기

    cv::waitKey(0); // 키 입력 기다리기 (무한 대기)
    return 0;
}
```
