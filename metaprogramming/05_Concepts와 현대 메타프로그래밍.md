# 📘 5장. Concepts와 현대 메타프로그래밍 기법

---

## 5.1 Concepts란 무엇인가?

### ✅ 정의

**Concepts**는 C++20에 도입된 기능으로,

> 템플릿 인자(T)로 **어떤 타입이 들어올 수 있는지를 명확하게 제한**하는 기능입니다.

### ✅ 목적

* 가독성 향상
* 명확한 오류 메시지 제공
* 의도에 맞는 타입만 허용하여 코드 안정성 강화

---

## 5.2 기본 제공 Concepts 예제

| Concept 이름                | 설명       | 예                         |
| ------------------------- | -------- | ------------------------- |
| `std::integral`           | 정수 타입    | `int`, `long`             |
| `std::floating_point`     | 실수 타입    | `float`, `double`         |
| `std::same_as<T>`         | 동일한 타입   | `std::same_as<int>`       |
| `std::derived_from<Base>` | 상속 여부 검사 | `std::derived_from<Base>` |

---

### ✅ 예: 정수 타입만 허용

```cpp
#include <concepts>

template<std::integral T>
T square(T x) {
    return x * x;
}

int main() {
    square(3);    // OK
    // square(3.14); // 오류: 실수는 정수 아님
}
```

---

## 5.3 사용자 정의 Concept

```cpp
template<typename T>
concept HasToString = requires(T a) {
    { a.toString() } -> std::convertible_to<std::string>;
};

struct MyClass {
    std::string toString() const { return "Hello"; }
};

template<HasToString T>
void printString(T obj) {
    std::cout << obj.toString() << '\n';
}
```

---

## 5.4 복합 조건 사용 (AND, OR, NOT)

### ✅ 예: `integral && copyable` 타입만 허용

```cpp
#include <concepts>

template<typename T>
concept MyConstraint = std::integral<T> && std::copyable<T>;

template<MyConstraint T>
T doubleValue(T x) {
    return x * 2;
}
```

---

## 5.5 Concepts vs SFINAE vs enable\_if

| 비교 항목  | Concepts | SFINAE (`enable_if`) |
| ------ | -------- | -------------------- |
| 코드 가독성 | 높음       | 낮음                   |
| 에러 메시지 | 명확       | 복잡                   |
| 문법 구조  | 직관적      | 복잡하고 장황함             |
| C++ 버전 | C++20\~  | C++11\~              |
| 추천 여부  | ✅ 적극 권장  | 제한적으로 사용             |

---

## 5.6 표준 라이브러리 활용 예시: `std::ranges`

```cpp
#include <ranges>
#include <vector>
#include <iostream>

void print_even(std::ranges::range auto&& r) {
    for (auto v : r | std::views::filter([](int x){ return x % 2 == 0; }))
        std::cout << v << ' ';
}
```

---

## 5.7 실습 문제

1. `std::floating_point` 타입만 허용하는 `divide(a, b)` 함수를 작성하시오.
2. `requires` 표현식을 사용하여 `.size()` 멤버 함수를 가진 타입만 허용하는 `printSize()` 함수를 작성하시오.
3. `HasBeginEnd` Concept을 정의하여 `begin()`과 `end()`가 있는 컨테이너만 출력하는 함수를 구현하시오.
4. `integral && sizeof(T) == 4` 조건을 만족하는 타입만 허용하는 함수 템플릿을 작성하시오.

---

## 5.8 정리

| 키워드             | 설명                                         |
| --------------- | ------------------------------------------ |
| `concept`       | 템플릿 타입 제약 조건 정의                            |
| `requires`      | 조건 표현식으로 Concept 정의 가능                     |
| `std::concepts` | 표준 제공 Concept: integral, floating\_point 등 |
| 장점              | 에러 메시지 명확, 코드 가독성 향상, 타입 안정성 강화            |

---

> 💡 **한 줄 요약**:
> *“Concepts는 템플릿을 더 안전하고 명확하게 만드는 현대 C++의 핵심 메타프로그래밍 도구이다.”*

---
