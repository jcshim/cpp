좋아요! Visual Studio Code(이하 VS Code)를 Windows PC에서 **C++ 개발용**으로 가장 간단하게 세팅하고 사용하는 방법을 단계별로 알려줄게요. 초심자도 따라 할 수 있도록 쉽게 설명할게요 😊

---

## ✅ 1. 필요한 것 설치하기

### ① **VS Code 설치**
- [https://code.visualstudio.com](https://code.visualstudio.com) 에서 VS Code 다운로드 후 설치

### ② **C++ 컴파일러 설치 (MinGW)**
- [https://www.mingw-w64.org/](https://www.mingw-w64.org/) 또는 아래 사이트에서 설치 프로그램 다운로드  
  👉 [MinGW-w64 Windows 설치](https://www.mingw-w64.org/downloads/)
- 설치 시:
  - Architecture: x86_64
  - Threads: posix
  - Exception: sjlj 또는 seh
  - Build revision은 기본값 그대로
- 설치 후, 예: `C:\Program Files\mingw-w64\...` 폴더 안에 `bin` 경로를 복사

### ③ **환경 변수 설정**
1. 윈도우 검색창에 **"환경 변수 편집"** 입력 → 클릭
2. **시스템 변수**에서 `Path` 선택 → **편집**
3. 아까 복사한 `...\bin` 경로를 **새로 추가**
4. 적용 후 확인

---

## ✅ 2. VS Code 세팅하기

### ① **C++ 확장 설치**
- VS Code 실행 → 왼쪽 사이드바 확장 아이콘(블럭 모양) 클릭
- 검색창에 `C/C++` 입력 → Microsoft가 만든 것 설치  
  (이름: **C/C++ by Microsoft**)

### ② (선택) **Code Runner 확장 설치**
- 여러 언어를 쉽게 실행할 수 있음 (초보자에게 추천)
- 검색창에 `Code Runner` 입력 → 설치

---

## ✅ 3. 첫 C++ 파일 실행하기

### ① 새 폴더 만들기 (예: `cpp-test`)
- 해당 폴더를 VS Code로 열기 (File → Open Folder)

### ② 새 파일 만들기
- 파일 이름: `hello.cpp`
```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello, C++ from VS Code!" << endl;
    return 0;
}
```

---

## ✅ 4. 프로그램 실행하기

### 방법 1: **터미널에서 직접 실행**
1. 터미널 열기: `Ctrl + ~`
2. 아래 명령어 입력:
```bash
g++ hello.cpp -o hello.exe
./hello.exe
```

### 방법 2: **Code Runner로 실행**
- `Ctrl + Alt + N` 누르기  
  (단, 이 방법은 Code Runner가 설치되어 있어야 함)

---

## 🎉 잘 되면 콘솔에:
```
Hello, C++ from VS Code!
```
가 출력됩니다!

---

## 💡 팁
- `tasks.json`, `launch.json` 등을 사용하면 디버깅도 가능하지만, 처음엔 위 방식만 알아도 충분합니다.
- C++ 문법 연습은 위 방식으로 충분히 가능해요!

필요하면 디버깅 방법이나 `tasks.json` 설정도 도와줄게요 🙂  
궁금한 점 있어?
