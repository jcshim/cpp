```
#include <opencv2/opencv.hpp>

int main()
{
    // 카메라 열기 (0: 첫 번째 카메라, 1: 두 번째 카메라, 2: 세 번째 카메라 ...)
    cv::VideoCapture cap(0); 
    if (!cap.isOpened())
    {
        return -1; // 카메라 열기 실패
    }

    cv::Mat frame;

    while (true)
    {
        cap >> frame; // 프레임 읽기
        if (frame.empty())
            break; // 읽기 실패하면 종료

        cv::imshow("Camera", frame); // 영상 출력

        if (cv::waitKey(1) == 27) // 'ESC' 키를 누르면 종료
            break;
    }

    cap.release(); // 카메라 해제
    cv::destroyAllWindows(); // 모든 윈도우 닫기

    return 0;
}

```
