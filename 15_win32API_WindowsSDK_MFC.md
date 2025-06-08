#  **Win32 API, Windows SDK, MFC**의 관계

---

## ✅ Win32 API vs Windows SDK vs MFC 비교표

| 항목         | **Win32 API**                          | **Windows SDK**                       | **MFC (Microsoft Foundation Classes)**    |
| ---------- | -------------------------------------- | ------------------------------------- | ----------------------------------------- |
| **정의**     | Windows OS 기능을 제어하는 **함수 집합**          | Windows 개발을 위한 **전체 도구 모음**           | Win32 API를 객체지향적으로 감싼 **C++ 클래스 라이브러리**   |
| **형태**     | C 기반 함수 (`MessageBox`, `CreateWindow`) | 헤더, 라이브러리, 컴파일러, 예제, 디버거 등 포함         | 클래스(`CWinApp`, `CDialog`, `CButton` 등) 형태 |
| **언어**     | 주로 C                                   | C/C++                                 | C++                                       |
| **목적**     | Windows 기능 직접 제어                       | 전체 Windows 애플리케이션 개발 지원               | Windows GUI 앱 개발을 **더 쉽게** 구현             |
| **포함 관계**  | SDK의 일부                                | Win32 API, MFC 포함                     | 내부적으로 Win32 API 호출                        |
| **복잡도**    | 복잡하고 세부 제어 가능                          | 낮음 (도구 자체이므로)                         | Win32보다 단순함                               |
| **개발 생산성** | 낮음                                     | 도구에 따라 다름                             | 상대적으로 높음                                  |
| **사용 예**   | `MessageBox()`, `CreateFile()` 등       | `windows.h`, `user32.lib`, `rc.exe` 등 | `CDialog`, `CView`, `CWinApp` 등           |
| **기반 시스템** | Windows OS                             | Windows OS + Visual Studio            | Windows SDK + Win32 API                   |
| **활용 분야**  | 저수준 시스템 제어, 드라이버, 성능 앱 등               | 모든 Windows 관련 개발                      | GUI 위주의 앱, 유지보수용 프로젝트 등                   |

---

## 🔁 포함 구조도 (관계 시각화)

```
Windows OS
 └── Windows API
      └── Win32 API
           └── MFC (Win32 기반 C++ 래퍼)
 └── Windows SDK
      ├── Win32 API 포함
      ├── MFC 포함
      ├── 개발 도구 포함 (compiler, linker 등)
```

---

## ✅ 요약 문장

* **Win32 API**는 Windows를 제어하기 위한 **기본 함수들**
* **Windows SDK**는 Win32 API를 포함한 전체 개발 툴킷
* **MFC**는 Win32 API를 객체지향적으로 다루기 쉽게 만든 **C++ 전용 프레임워크**
