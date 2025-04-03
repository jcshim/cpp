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

C++에서 **제너릭 프로그래밍(Generic Programming)**은 **데이터 타입에 관계없이 재사용 가능한 코드**를 작성하는 프로그래밍 방식이야. 쉽게 말해서, 하나의 함수나 클래스를 다양한 데이터 타입에 대해 **동일한 방식으로 동작하도록 만드는 것**이지.

이를 위해 **템플릿(template)**을 사용해. 함수 템플릿이나 클래스 템플릿으로 정의해두면, 나중에 어떤 타입을 넣어도 그에 맞게 동작하게 만들어줘.

---

### ✅ 예제 1: 함수 템플릿
```cpp
#include <iostream>
using namespace std;

template <typename T>
T add(T a, T b) {
    return a + b;
}

int main() {
    cout << add(3, 4) << endl;       // int형
    cout << add(2.5, 3.1) << endl;   // double형
    return 0;
}
```

✔️ 위 코드는 `int`, `double` 등 다양한 타입에 대해 `add()` 함수를 재사용할 수 있어.

---

### ✅ 예제 2: 클래스 템플릿
```cpp
template <typename T>
class Pair {
private:
    T first, second;
public:
    Pair(T a, T b) : first(a), second(b) {}
    T getMax() {
        return (first > second) ? first : second;
    }
};

int main() {
    Pair<int> p1(10, 20);
    cout << p1.getMax() << endl;

    Pair<double> p2(3.14, 2.71);
    cout << p2.getMax() << endl;
}
```

✔️ 클래스도 마찬가지로 여러 타입을 받아서 재사용할 수 있게 해주는 게 제너릭 프로그래밍이야.

---

### 🔍 요약

| 구분 | 설명 |
|------|------|
| **목적** | 다양한 타입에 대해 하나의 코드로 처리 |
| **도구** | 템플릿(template) 사용 |
| **장점** | 코드 재사용성 증가, 유지보수 용이 |
| **사용 예** | 컨테이너 클래스(STL), 정렬 함수, 자료구조 등 |

---

필요하다면 STL에서 `vector`, `map`, `sort()` 같은 것도 전부 제너릭 프로그래밍의 결과물이야. 더 깊이 들어가고 싶으면 알려줘!

### 📌 왜 유용할까?

- `int`, `double`, `char` 등 자료형별로 함수 하나씩 만들 필요 없음
- 유지보수 쉬움, 중복 코드 줄어듦
- C++의 STL (벡터, 리스트 등)도 전부 템플릿 기반이에요!
