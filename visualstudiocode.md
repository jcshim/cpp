물론이죠! **초보자도 따라할 수 있도록** 아주 쉽게, **Visual Studio Community 설치부터 Visual Studio Code(이하 VS Code)에서 C++ 개발 환경을 설정하는 전체 과정을 단계별로 정리**해드릴게요 😊

---

# ✅ 1단계: Visual Studio Community 설치

### 🎯 목적: C++ 컴파일러 설치 (MSVC)

---

### ✔ 1. [Visual Studio Community](https://visualstudio.microsoft.com/ko/vs/community/) 사이트에 접속

- 주소: https://visualstudio.microsoft.com/ko/vs/community/
- 💡 무료 버전이므로 걱정 없이 설치 가능!

---

### ✔ 2. 설치 파일 다운로드 및 실행

- `무료 다운로드` 버튼 클릭 → 설치 프로그램 실행

---

### ✔ 3. 설치 구성 선택

- 설치 화면에서 **"C++를 사용한 데스크톱 개발"** 선택 ✅  
  (이게 C++ 컴파일러와 필수 도구를 포함함)
- 오른쪽 아래에 있는 **“설치” 버튼 클릭**

---

### ✔ 4. 설치 완료 후 재부팅 (필요시)

- 설치가 완료되면 재부팅을 요청할 수도 있어요.
- **재부팅 후 자동으로 Visual Studio가 열릴 수 있음** (닫아도 됨!)

---

## 🎉 이로써 컴퓨터에 **C++ 컴파일러(MSVC)**가 설치 완료!

---

# ✅ 2단계: Visual Studio Code 설치

---

### ✔ 1. [VS Code 공식 홈페이지](https://code.visualstudio.com) 접속

- 주소: https://code.visualstudio.com

---

### ✔ 2. 운영체제에 맞는 VS Code 설치

- Windows용 다운로드 → 설치 파일 실행 → 설치 완료

---

### ✔ 3. VS Code 실행

- 처음 실행하면 아주 간단한 화면이 나옴

---

# ✅ 3단계: C++ 개발 확장팩 설치 (VS Code에서)

---

### ✔ 1. 좌측 메뉴에서 퍼즐 아이콘(확장) 클릭

- 또는 `Ctrl + Shift + X` 누르기

---

### ✔ 2. 검색창에 `C++` 입력

- **C/C++ (by Microsoft)** 확장 설치  
  👉 파란색 “설치” 버튼 클릭

---

### ✔ 3. 추가 추천 확장 (선택사항)
- CMake Tools (필요시)
- Code Runner (간단 실행용)

---

# ✅ 4단계: C++ 파일 생성 및 빌드 환경 설정

---

### ✔ 1. 폴더 열기

- `파일 > 폴더 열기` → 원하는 폴더 선택  
  (C++ 파일을 저장할 폴더)

---

### ✔ 2. 새 파일 만들기

- `main.cpp` 같은 이름으로 새 파일 생성  
- 예시 코드 입력:
```cpp
#include <iostream>
int main() {
    std::cout << "Hello, C++!\n";
    return 0;
}
```

---

### ✔ 3. 컴파일러 경로 자동 인식 확인

- 파일 저장 → VS Code 오른쪽 아래에 “컴파일러 설치됨” 문구가 보일 수도 있음

---

### ✔ 4. 빌드/실행을 위한 `tasks.json` 설정 (한 번만 설정)

1. 메뉴에서 `Terminal > Configure Tasks...` 클릭  
2. **“Create tasks.json file from template” 선택**  
3. **“Others” 선택**  
4. 아래와 같이 수정:

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "build C++",
      "type": "shell",
      "command": "cl",
      "args": [
        "/EHsc",
        "main.cpp"
      ],
      "group": {
        "kind": "build",
        "isDefault": true
      }
    }
  ]
}
```

💡 위에서 `cl`은 MSVC 컴파일러이며, `main.cpp`는 파일 이름입니다.

---

### ✔ 5. 실행 방법

1. `Ctrl + Shift + B` → 빌드 시작  
2. `main.exe`가 생성됨 → **터미널에 직접 실행 명령 입력:**
```
main
```

✔ 또는 Code Runner 확장 설치 후 오른쪽 위 ▶ 버튼으로 실행

---

## 🎯 최종 결과

- **VS Code에서 C++ 파일을 작성하고**
- **Visual Studio Community에서 제공한 컴파일러로 빌드/실행 가능!**

---

# 📝 요약 순서

| 단계 | 설명 |
|------|------|
| 1단계 | Visual Studio Community 설치 (C++ 포함 선택) |
| 2단계 | VS Code 설치 |
| 3단계 | C++ 확장 설치 (C/C++ by Microsoft) |
| 4단계 | `main.cpp` 작성 및 빌드 설정 |
| 5단계 | `Ctrl + Shift + B`로 빌드, `main` 명령으로 실행 |

---

필요하시면 MinGW 컴파일러 기반 설치법도 정리해드릴 수 있어요! 😊
