# 템플릿(Template)은 C++에서 제네릭 프로그래밍을 가능하게 해준다.
##  하나의 코드로 **여러 자료형에 대해 동작하는 함수나 클래스**를 만들 수 있음
### 재사용성도 높아지고 깔끔해진다.

---

### ✅ 간단한 예제: 두 값 중 큰 값을 반환하는 함수

```cpp
#include <iostream>
using namespace std;

// 템플릿 함수 정의
template <typename T>
T getMax(T a, T b) {
    return (a > b) ? a : b;
}

int main() {
    cout << getMax(10, 20) << endl;       // int
    cout << getMax(3.14, 2.71) << endl;   // double
    cout << getMax('a', 'z') << endl;     // char

    return 0;
}
```

---

### 🧠 설명

- `template <typename T>`: **T는 자료형의 자리 표시자(placeholder)**입니다. 컴파일러가 함수가 호출될 때 T에 해당하는 실제 타입을 자동으로 넣어줍니다.
- `getMax()` 함수는 T 타입 두 개를 받아서, 더 큰 값을 리턴합니다.
- `main()`에서는 `int`, `double`, `char` 자료형에 대해 같은 함수를 재사용하고 있어요!

---

### 📌 왜 유용할까?

- `int`, `double`, `char` 등 자료형별로 함수 하나씩 만들 필요 없음
- 유지보수 쉬움, 중복 코드 줄어듦
- C++의 STL (벡터, 리스트 등)도 전부 템플릿 기반이에요!
