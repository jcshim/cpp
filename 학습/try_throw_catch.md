## ✅ 가장 쉬운 예제: 파일 읽기 + 예외 처리

```cpp
#include <iostream>
#include <fstream>  // fstream
#include <stdexcept> // runtime_error

int main() {
    std::ifstream file("hello.txt");  // 파일 열기 시도

    if (!file.is_open()) {
        // 파일이 없으면 예외 던지기
        throw std::runtime_error("파일을 열 수 없습니다!");
    }

    std::string line;
    while (std::getline(file, line)) {
        std::cout << line << std::endl;  // 한 줄씩 출력
    }

    file.close();  // 파일 닫기
    return 0;
}
```

이건 예외 처리 없이 단순히 `throw`만 쓴 거예요. 이걸 try-catch로 감싸면?

---

## 🔒 예외를 안전하게 처리하려면: try-catch 사용

```cpp
#include <iostream>
#include <fstream>
#include <stdexcept>

int main() {
    try {
        std::ifstream file("hello.txt");
        if (!file.is_open()) {
            throw std::runtime_error("파일을 열 수 없습니다!");
        }

        std::string line;
        while (std::getline(file, line)) {
            std::cout << line << std::endl;
        }

        file.close();
    } catch (const std::exception& e) {
        std::cout << "오류 발생: " << e.what() << std::endl;
    }

    return 0;
}
```

---

## 📌 무슨 일이 일어나냐면?

1. `"hello.txt"` 파일을 열려고 시도함
2. 없으면 `throw`로 예외를 발생시킴
3. `catch` 블록에서 그 오류 메시지를 받아서 출력함

---

## 📁 실습 팁

1. 같은 폴더에 `hello.txt` 파일을 하나 만들어서
2. 안에 `"Hello, world!"` 같은 글 써놓고
3. 위 코드를 실행해보세요!
