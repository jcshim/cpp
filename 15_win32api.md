# **Win32 API**
**개념 이해 → 구조 → 핵심 함수 → 간단한 예제 → 현대 기술과의 연결** 

---

## 🧠 Win32 API 1시간 소개용 핵심 내용

---

### ✅ 1. Win32 API란 무엇인가?

* **Windows 운영체제에서 직접 제공하는 API(Application Programming Interface)**
* C 기반의 함수 호출을 통해 **윈도우 창, 버튼, 메시지 처리, 파일 I/O 등** 시스템 자원을 제어
* GUI 뿐 아니라, **메모리, 프로세스, 스레드, 네트워크 등** 저수준 기능도 제공

> 🎯 "C++에서 운영체제와 직접 대화하는 방법"

---

### ✅ 2. Win32 API vs MFC vs .NET

| 구분            | 설명                                   |
| ------------- | ------------------------------------ |
| **Win32 API** | 가장 낮은 수준, 순수 C 함수 기반, 속도와 제어력 최고     |
| **MFC**       | Win32 API를 클래스 기반으로 추상화한 C++ 프레임워크   |
| **.NET/WPF**  | 고수준 UI, 자동 메모리 관리, 생산성 중심 (.NET 플랫폼) |

---

### ✅ 3. Win32 API 프로그램 구조

```cpp
#include <windows.h>

// WinMain: 진입점
int WINAPI WinMain(HINSTANCE hInstance, HINSTANCE hPrev, LPSTR lpCmdLine, int nCmdShow) {
    MessageBox(NULL, "Hello Win32 API!", "Sample", MB_OK);
    return 0;
}
```

* `WinMain`은 Win32 GUI 프로그램의 시작점
* `MessageBox`는 가장 대표적인 Win32 함수
* `HINSTANCE`, `LPSTR`, `HWND` 등은 Win32 전용 타입

---

### ✅ 4. 메시지 기반 구조

* Win32는 **이벤트 중심(Message Loop)** 으로 동작

```cpp
MSG msg;
while (GetMessage(&msg, NULL, 0, 0)) {
    TranslateMessage(&msg);
    DispatchMessage(&msg);
}
```

* `GetMessage` → 이벤트를 기다림
* `DispatchMessage` → 처리할 윈도우 함수로 전달

---

### ✅ 5. 윈도우 창 생성 예제 (기초 버전)

```cpp
#include <windows.h>

LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);

int WINAPI WinMain(HINSTANCE h, HINSTANCE, LPSTR, int) {
    WNDCLASS wc = {0};
    wc.lpfnWndProc = WndProc;
    wc.hInstance = h;
    wc.lpszClassName = "MyWndClass";
    RegisterClass(&wc);

    HWND hwnd = CreateWindow("MyWndClass", "Win32 창", WS_OVERLAPPEDWINDOW,
        100, 100, 400, 300, NULL, NULL, h, NULL);

    ShowWindow(hwnd, SW_SHOW);

    MSG msg;
    while (GetMessage(&msg, NULL, 0, 0)) {
        TranslateMessage(&msg);
        DispatchMessage(&msg);
    }

    return 0;
}

LRESULT CALLBACK WndProc(HWND hwnd, UINT msg, WPARAM w, LPARAM l) {
    if (msg == WM_DESTROY) PostQuitMessage(0);
    return DefWindowProc(hwnd, msg, w, l);
}
```

✅ 핵심 흐름:

1. `WNDCLASS` 등록
2. `CreateWindow`로 창 생성
3. 메시지 루프 처리
4. `WndProc` 함수에서 메시지 대응

---

### ✅ 6. 자주 사용하는 Win32 API 함수

| 함수                       | 역할         |
| ------------------------ | ---------- |
| `CreateWindow`           | 창 생성       |
| `ShowWindow`             | 창 보여주기     |
| `MessageBox`             | 메시지 박스 띄우기 |
| `GetMessage`             | 메시지 받기     |
| `SendMessage`            | 메시지 직접 전달  |
| `LoadIcon`, `LoadCursor` | 리소스 불러오기   |
| `CreateFile`, `ReadFile` | 파일 입출력     |
| `CreateThread`           | 스레드 생성     |

---

### ✅ 7. Win32의 장단점

| 장점                   | 단점              |
| -------------------- | --------------- |
| 성능 최고, 하드웨어 접근 가능    | 코드가 복잡하고 난해함    |
| 운영체제와 직접 연결          | 생산성이 낮음         |
| 실제 산업/게임 엔진에서 여전히 사용 | 현대 GUI 트렌드에 부적합 |

---

### ✅ 8. 학습용 예제 추천

* `MessageBox()`로 간단한 프로그램 만들기
* `CreateWindow`로 사용자 창 만들고 닫기 구현
* 버튼 추가 + `WM_COMMAND` 메시지 처리 실습 (2시간 연장 시 적합)

---

### ✅ 9. 수업 정리용 마무리 요약

```markdown
- Win32 API는 Windows 운영체제에서 C/C++로 시스템과 GUI를 제어할 수 있는 저수준 API입니다.
- C++에서는 직접 제어가 가능한 대신, 복잡한 구조와 메시지 루프 개념이 중요합니다.
- MFC나 .NET과 비교하면 성능은 뛰어나지만 생산성은 낮습니다.
- GUI뿐 아니라 파일, 네트워크, 스레드 등 시스템 전반을 통제할 수 있는 강력한 도구입니다.
```

---
