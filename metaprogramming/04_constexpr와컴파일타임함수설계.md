# 📘 4장. `constexpr`와 컴파일 타임 함수 설계

---

## 4.1 `constexpr`란 무엇인가?

### ✅ 정의

`constexpr`는 C++11부터 도입된 키워드로,

> **컴파일 타임에 계산될 수 있는 값 또는 함수**를 정의합니다.

### ✅ 특징

* 컴파일러가 결과를 미리 계산해 코드에 삽입 가능
* 함수와 변수 모두에 사용 가능
* C++14 이후, **다중 문장**, **조건문**, **루프** 등도 허용됨

---

### ✅ 예제: `constexpr` 함수

```cpp
constexpr int square(int x) {
    return x * x;
}

int main() {
    constexpr int a = square(5); // 컴파일 타임에 25로 계산됨
}
```

---

## 4.2 `consteval`: 무조건 컴파일 타임 실행 (C++20\~)

### ✅ 정의

> `consteval`은 \*\*"컴파일 타임에 반드시 실행되어야 하는 함수"\*\*입니다.

```cpp
consteval int doubleVal(int x) {
    return x * 2;
}

int main() {
    constexpr int y = doubleVal(10);  // OK
    // int z = doubleVal(someRuntimeValue); // 오류 발생
}
```

---

## 4.3 `constinit`: 정적 변수 초기화 명시 (C++20\~)

### ✅ 정의

`constinit`은 **정적/전역 변수의 초기화를 컴파일 타임에 보장**하기 위해 사용됩니다.

```cpp
constexpr int getVal() { return 42; }
constinit int global = getVal(); // 컴파일 타임 초기화 보장
```

---

## 4.4 `constexpr`와 템플릿 메타함수 비교

| 항목     | `template` 메타함수 | `constexpr` 함수  |
| ------ | --------------- | --------------- |
| 선언 방식  | 구조체/클래스         | 일반 함수           |
| 구문 복잡성 | 높음 (재귀 필요)      | 낮음 (일반 함수처럼 사용) |
| 디버깅    | 어려움             | 쉬움              |
| 루프 사용  | 불가능             | 가능 (C++14 이상)   |
| 직관성    | 낮음              | 높음              |

---

## 4.5 혼합 설계: 런타임 + 컴파일 타임 함수

### ✅ 예제: 둘 다 사용

```cpp
constexpr int factorial(int n) {
    int res = 1;
    for (int i = 2; i <= n; ++i)
        res *= i;
    return res;
}

int main() {
    int x;
    std::cin >> x;
    int a = factorial(x);        // 런타임 실행
    constexpr int b = factorial(5); // 컴파일 타임 실행
}
```

---

## 4.6 실습 문제

1. `constexpr`로 구현한 `isPrime(n)` 함수를 작성하시오.
2. `consteval`을 사용하여 문자열 길이를 컴파일 타임에 계산하는 함수 `strLength`를 작성하시오.
3. `constinit` 키워드로 전역 상수를 초기화하되, `constexpr` 함수의 결과를 활용해보시오.
4. `constexpr`을 활용한 `fibonacci(n)` 함수 작성 (반복문 기반)

---

## 4.7 정리

| 키워드         | 설명                        |
| ----------- | ------------------------- |
| `constexpr` | 컴파일 타임 실행 가능한 함수/변수 (선택적) |
| `consteval` | 무조건 컴파일 타임에 실행되는 함수       |
| `constinit` | 전역/정적 변수의 컴파일 타임 초기화를 보장  |

---

> 💡 **한 줄 요약**:
> *“`constexpr` 계열 키워드는 성능을 높이고 오류를 줄이는 컴파일 타임 설계를 가능하게 한다.”*

---

