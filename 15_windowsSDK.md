# **Windows SDK(Software Development Kit)**

---

## ✅ Windows SDK란?

**Windows SDK (Software Development Kit)** 는
Windows 운영체제에서 **소프트웨어를 개발하기 위한 전체 도구 모음**입니다.
여기에는 다음과 같은 요소들이 포함되어 있습니다:

| 구성 요소     | 설명                                                 |
| --------- | -------------------------------------------------- |
| **헤더 파일** | `windows.h` 등 – Win32 API 정의 포함                    |
| **라이브러리** | `user32.lib`, `gdi32.lib` 등 – API 구현과 연결           |
| **도구들**   | 컴파일러(`cl.exe`), 리소스 컴파일러(`rc.exe`), 링커(`link.exe`) |
| **문서/예제** | MSDN 문서, 샘플 코드, 도움말                                |
| **디버깅 툴** | `windbg`, 성능 분석 도구                                 |

> 🔧 즉, **Windows용 프로그램을 만들기 위해 필요한 모든 “부품 + 설명서 + 도구”의 집합**

---

## ✅ Windows SDK가 왜 필요한가?

Windows 운영체제에서는 GUI, 파일 처리, 메모리 관리, 네트워크 등
모든 기능을 **Windows API**라는 이름의 함수로 제공합니다.

👉 하지만 이 API를 사용하려면 다음이 필요합니다:

* 헤더(`windows.h`)에서 함수 정의
* 라이브러리(`.lib`) 파일과 링커 연결
* 컴파일 및 실행 도구

이 모든 것을 통합해서 제공하는 것이 바로 **Windows SDK**입니다.

---

## ✅ 주요 구성 요소

| 구성 요소    | 대표 예                           | 설명                 |
| -------- | ------------------------------ | ------------------ |
| 헤더 파일    | `windows.h`, `winuser.h` 등     | 함수/상수/구조체 정의       |
| 라이브러리 파일 | `kernel32.lib`, `user32.lib` 등 | API 구현 연결용         |
| 도구       | `cl.exe`, `rc.exe`, `link.exe` | 컴파일, 링크, 리소스 처리 도구 |
| 문서       | MSDN, HTML/CHM 형식 문서           | API 사용법 설명         |
| 샘플 코드    | Windows Forms, DirectX 예제 등    | 학습용 샘플 코드          |

---

## ✅ SDK는 어디에 설치되나?

Visual Studio를 설치하면 자동으로 Windows SDK도 설치됨
(예: `C:\Program Files (x86)\Windows Kits\10`)

---

## ✅ Windows SDK의 사용 예

### 📄 예: Hello Win32 메시지 박스

```cpp
#include <windows.h>

int WINAPI WinMain(HINSTANCE h, HINSTANCE, LPSTR, int) {
    MessageBox(NULL, "Hello, Windows SDK!", "Notice", MB_OK);
    return 0;
}
```

이 코드는 다음을 필요로 함:

* `windows.h` → SDK의 헤더
* `user32.lib` → SDK의 라이브러리
* `cl.exe`, `link.exe` → SDK의 빌드 도구

---

## ✅ Windows SDK의 대상 플랫폼

* **Win32 / Win64 데스크탑 애플리케이션**
* **UWP 앱 (Universal Windows Platform)**
* **DirectX 기반 게임/그래픽 앱**
* **Windows Driver 개발용 WDK (확장 SDK)**

---

## ✅ 최신 버전 정보 (2025 기준)

* **Windows 10 SDK / Windows 11 SDK**가 Visual Studio 2022/2025와 함께 사용됨
* 버전별로 다양한 API와 기능 추가 (예: WinUI 3, Project Reunion 등 포함)

---

## ✅ 요약 정리

> Windows SDK는 Windows 운영체제에서 C/C++ 기반 애플리케이션을 개발하기 위한 모든 개발 도구(헤더, 라이브러리, 컴파일러, 문서 등)를 포함한 통합 개발 환경이다.

---
