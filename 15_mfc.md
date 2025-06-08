# MFC 소개
---

## 🧠 MFC 핵심 개념 요약

### ✅ 1. MFC란 무엇인가?

* **Microsoft Foundation Classes**
* Microsoft가 제공한 **C++ 기반 윈도우 GUI 애플리케이션 프레임워크**
* **Win32 API를 객체지향적으로 감싸서 쉽게 사용**할 수 있도록 한 라이브러리

> 🎯 목적: 복잡한 WinAPI 호출을 숨기고 클래스 기반으로 GUI 프로그래밍을 쉽게 함

---

### ✅ 2. MFC의 주요 특징

| 특징                  | 설명                                               |
| ------------------- | ------------------------------------------------ |
| 객체지향 구조             | 윈도우 창, 버튼 등을 클래스(`CWnd`, `CButton`)로 제공          |
| 이벤트 기반 프로그래밍        | 메시지 맵(`ON_WM_PAINT`, `ON_BN_CLICKED`)을 통해 이벤트 처리 |
| 문서/뷰 구조 지원          | `Document/View Architecture`로 데이터-UI 분리          |
| Visual Studio 통합 개발 | 클래스 마법사, 리소스 에디터로 GUI 구성 가능                      |

---

### ✅ 3. 주요 클래스 구조

* `CWinApp` : 응용프로그램 전체를 관리
* `CFrameWnd` : 메인 프레임 윈도우
* `CView` : 데이터를 화면에 보여주는 뷰 클래스
* `CDocument` : 데이터 저장 및 관리
* `CDialog` : 대화상자 기반 UI 구현
* `CWnd` : 모든 윈도우 요소의 기반 클래스

---

### ✅ 4. MFC의 기본 구조 예

```cpp
class CMyApp : public CWinApp {
public:
    BOOL InitInstance() {
        CFrameWnd* pFrame = new CFrameWnd;
        pFrame->Create(NULL, _T("MFC 예제 윈도우"));
        pFrame->ShowWindow(SW_SHOW);
        m_pMainWnd = pFrame;
        return TRUE;
    }
};

CMyApp theApp;
```

* `CWinApp` 상속 → 앱 전체를 정의
* `CFrameWnd` 생성 → 창 생성
* `ShowWindow()` → 화면에 표시

---

### ✅ 5. MFC 메시지 맵 (Message Map)

* MFC는 **윈도우 메시지**를 **함수로 매핑**해서 처리

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CFrameWnd)
    ON_WM_PAINT()
END_MESSAGE_MAP()

void CMyWnd::OnPaint() {
    CPaintDC dc(this);
    dc.TextOutW(100, 100, _T("Hello MFC!"));
}
```

---

### ✅ 6. MFC 프로젝트 종류

* **Dialog-based App**: 버튼, 텍스트 상자 중심의 간단한 앱
* **SDI (Single Document Interface)**: 하나의 문서만 열 수 있음
* **MDI (Multiple Document Interface)**: 여러 문서를 동시에 열 수 있음

---

### ✅ 7. MFC의 장단점

| 장점                    | 단점                    |
| --------------------- | --------------------- |
| Windows에 최적화된 성능      | Windows 전용 (멀티 플랫폼 X) |
| Visual Studio와 강력한 통합 | 최신 UI 트렌드와 거리가 있음     |
| Win32 API 대비 단순화된 구조  | 러닝커브가 존재함             |

---

### ✅ 8. MFC의 현재와 미래

* **레거시 유지보수**에 여전히 많이 사용됨 (기존 산업용/국방 시스템 등)
* 새로운 UI 개발은 **WinForms, WPF, Qt, .NET MAUI** 등으로 이동
* 그러나 **Visual Studio는 여전히 MFC 지원 중**이고, 국내 기업(대기업 SI, 공공기관 등)에서 일부 사용

---

### 🔧 9. 추천 데모 (10분)

* Visual Studio에서 "MFC App Wizard"를 통해 Dialog 기반 프로젝트 생성
* 버튼 클릭 → `MessageBox()` 띄우기 실습

---

### 📚 강의 정리용 요약 슬라이드 문구

```markdown
- MFC는 C++ 기반의 Microsoft GUI 애플리케이션 프레임워크이다.
- 복잡한 WinAPI를 객체지향적으로 추상화하여 손쉽게 윈도우 GUI 프로그래밍 가능.
- `CWinApp`, `CWnd`, `CDialog`, `CFrameWnd` 등의 핵심 클래스로 구성.
- 메시지 맵(Message Map)을 통해 이벤트 기반 프로그래밍을 구현.
- 현재는 유지보수 및 기존 시스템 중심으로 활용되며, 학습 목적이나 공공/산업용 프로젝트에 유효.
```
