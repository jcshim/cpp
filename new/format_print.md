C++20부터 `std::format`, C++23부터는 `std::print`가 추가되어 **Python의 f-string 스타일 출력**이 가능해졌습니다. 아래는 각각의 예제입니다:

---

### ✅ `std::format` (C++20)
```cpp
#include <iostream>
#include <format> // C++20

int main() {
    int age = 25;
    std::string name = "Alice";

    std::string result = std::format("My name is {} and I am {} years old.", name, age);
    std::cout << result << std::endl;
    return 0;
}
```

📌 출력:
```
My name is Alice and I am 25 years old.
```

---

### ✅ `std::print` (C++23)
```cpp
#include <print> // C++23

int main() {
    int a = 5, b = 10;
    std::print("Sum of {} and {} is {}\n", a, b, a + b);
    return 0;
}
```

📌 출력:
```
Sum of 5 and 10 is 15
```

---

### 🧠 주요 특징
- `{}` 위치에 값 자동 삽입 (Python `f"{}"` 스타일)
- 숫자 정렬, 소수점 제어 등 포맷 지정도 가능

```cpp
#include <format>
#include <iostream>

int main() {
    double pi = 3.14159;
    std::cout << std::format("Pi to 2 decimals: {:.2f}", pi) << std::endl;
    return 0;
}
```

📌 출력:
```
Pi to 2 decimals: 3.14
```

---

필요하시면 `std::format`을 활용한 날짜, 정렬, 진수 출력 등 고급 포맷 예제도 드릴 수 있어요!
