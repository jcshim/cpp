# 함수 오버로딩과 함수 템플릿을 단계적으로 설명

---

## 🧱 1단계: 정수와 실수를 변수에 담고 더하기  
```cpp
int a1 = 2, a2 = 3;
double f1 = 2.2, f2 = 3.3;
std::cout << a1 + a2 << '\n'; // 5
std::cout << f1 + f2 << '\n'; // 5.5
```
- 정수형 `int`와 실수형 `double`을 각각 **직접 더한** 예제
- ✅ 간단한 기본 연산

---

## 🧱 2단계: 함수로 분리해서 더하기  
```cpp
int Add1(int a, int b) { return a + b; }
double Add2(double a, double b) { return a + b; }
```
- 정수끼리 더할 땐 `Add1`, 실수끼리는 `Add2` 함수를 호출  
- ❗ **함수 이름이 달라서 일일이 만들어야 함**

---

## 🧱 3단계: 함수 이름은 같고, 매개변수로 구분! → **함수 오버로딩**
```cpp
int Add(int a, int b) { return a + b; }
double Add(double a, double b) { return a + b; }
```

- ✔️ 함수 이름이 `Add`로 **같지만**, 매개변수 타입이 달라서 컴파일러가 알아서 구분
- 이게 바로 **함수 오버로딩 (Function Overloading)**!
- **같은 기능, 다른 타입** → 코드가 더 간결해짐

> 📌 함수 오버로딩이란?
> 👉 함수 이름은 같게, 매개변수(타입이나 개수)가 다르게 만들어 사용하는 것!

---

## 🧱 4단계: 템플릿으로 더 쉽게! → **함수 템플릿**
```cpp
template <typename T>
T Add(T a, T b) {
    return a + b;
}
```

- `T`는 타입을 의미하는 **형식 매개변수(Type Parameter)**  
- `int`, `double`, `float` 등 다양한 타입에 대해 **하나의 함수만** 만들면 됨!
- 컴파일러가 알아서 `T`에 타입을 넣어줌

> 📌 함수 템플릿이란?
> 👉 타입을 일반화해서, 하나의 함수로 다양한 자료형을 처리하는 방식

---

## ✅ 핵심 비교 요약

| 방식 | 설명 | 예시 |
|------|------|------|
| 일반 함수 | 자료형마다 따로 함수 작성 | `Add1(int, int)` / `Add2(double, double)` |
| 함수 오버로딩 | 같은 이름, 매개변수 타입으로 구분 | `Add(int, int)` / `Add(double, double)` |
| 함수 템플릿 | 타입을 일반화해서 하나의 함수로 처리 | `template <typename T> T Add(T, T)` |

---

## 🎯 한 줄 요약!

> 🔧 **함수 오버로딩**: “자료형별로 같은 기능을 이름 하나로!”  
> 🧪 **함수 템플릿**: “자료형을 가리지 않고, 하나의 함수로!”

---

필요하시면 템플릿을 이용한 클래스 정의, 복잡한 타입 사용 예제도 추가로 정리해드릴 수 있어요! 😊
