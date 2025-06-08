# C++을 기반으로 한 Windows UI 기술의 발전 

---

## 🕰️ C++ 기반 Windows UI 기술의 발전 순서

| 시대            | 기술 이름                                     | 설명                                                                   |
| ------------- | ----------------------------------------- | -------------------------------------------------------------------- |
| ① **1990s 초** | **Win32 API**                             | 가장 저수준의 Windows GUI 함수 집합. C 기반, 고성능.                                |
| ② **1992\~**  | **MFC (Microsoft Foundation Classes)**    | Win32 API를 C++로 객체지향적으로 감싼 라이브러리.                                    |
| ③ **2002\~**  | **Windows Forms (WinForms)**              | .NET Framework 기반의 이벤트 중심 GUI 프레임워크 (C#, VB.NET 중심).                 |
| ④ **2006\~**  | **WPF (Windows Presentation Foundation)** | XAML 기반의 .NET 고급 UI 프레임워크. 벡터 그래픽, 데이터 바인딩, MVVM 등 지원.               |
| ⑤ **2012\~**  | **Windows 8 Metro / WinRT**               | UWP 전신. WinRT 기반, 샌드박스 구조. Windows Store 앱 중심.                       |
| ⑥ **2015\~**  | **UWP (Universal Windows Platform)**      | 다양한 디바이스용 앱(PC, Xbox, HoloLens) 통합 개발 플랫폼. XAML 기반, C++/CX, C# 등 사용. |
| ⑦ **2021\~**  | **WinUI 3**                               | Win32 + UWP를 통합한 최신 UI 프레임워크. XAML 기반, C++/WinRT, .NET 모두 지원.        |
| ⑧ **현재/미래**   | **Windows App SDK** (Project Reunion)     | WinUI 3 포함. Win32/UWP 통합 SDK. Win11 이후 표준 앱 플랫폼.                     |

---

## 🔁 계보 흐름 요약

```
C 기반
└── Win32 API (1990s)
    └── MFC (C++ Wrapper)
.NET 기반
└── WinForms → WPF → UWP
XAML 기반 통합
└── UWP → WinUI 3 → Windows App SDK (통합 플랫폼)
```

---

## ⏱️ 시간 순서로 보기

```text
[1990] Win32 API
   ↓
[1992] MFC (C++)
   ↓
[2002] WinForms (.NET)
   ↓
[2006] WPF (.NET + XAML)
   ↓
[2012] Metro/WinRT (Windows 8 앱)
   ↓
[2015] UWP (Windows 10)
   ↓
[2021] WinUI 3
   ↓
[2021~] Windows App SDK (Reunion 통합)
```

---

## 🔍 기타 기술 및 연결

| 기술                  | 특징 및 관련성                                             |
| ------------------- | ---------------------------------------------------- |
| **C++/CX**          | UWP용 C++ 확장 문법 (MS 전용). 현재는 C++/WinRT로 대체됨.          |
| **C++/WinRT**       | UWP 및 WinUI 3의 표준 네이티브 C++ 바인딩 방식.                   |
| **XAML**            | WPF, UWP, WinUI에서 공통으로 쓰이는 UI 정의 언어.                 |
| **Windows App SDK** | WinUI 3 포함, Win32 + UWP 기능 통합용 패키지. 사실상 WinUI 3의 기반. |

---

## ✅ 요약 문장 (정리용)

> C++ 기반 Windows UI 기술은 **Win32 API → MFC → .NET 진영 (WinForms, WPF) → UWP → WinUI 3**로 발전해왔으며, 현재는 이들을 통합한 **Windows App SDK**를 중심으로 정리되고 있습니다.
