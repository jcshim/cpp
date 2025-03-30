# const "변하지 않는 값"

---

## ✅ 1. **실수로 값을 바꾸지 않게 막기 위해!**

```cpp
void printValue(const int x) {
    // x = 10; // 에러! x는 const니까 바꿀 수 없어
    std::cout << x << std::endl;
}
```

### 💡 왜 필요해?
- 함수 안에서 **변경되면 안 되는 값**이 실수로 바뀌는 걸 **방지**해줘.
- 코드의 **의도를 분명히 보여줌**: "이건 절대 안 바뀐다!"

---

## ✅ 2. **코드의 안정성과 가독성을 높이기 위해!**

```cpp
const double PI = 3.141592;
```

### 💡 왜 필요해?
- `PI` 같은 값은 **절대 바뀌면 안 되는 상수**야.
- `const`를 써주면 누가 봐도 "이 값은 고정이구나!" 하고 알 수 있어.
- 나중에 실수로 바꾸려 하면 **컴파일러가 에러**로 알려줘.

---

## ✅ 3. **포인터, 참조, 클래스와 같이 쓸 때 유용해!**

### 📌 포인터 예시
```cpp
const int* p = &a; // 포인터가 가리키는 값은 못 바꿈
int* const p = &a; // 포인터 자체는 못 바꿈 (주소 못 바꿈)
const int* const p = &a; // 둘 다 못 바꿈
```

### 📌 참조 예시
```cpp
void printValue(const int& ref) {
    // ref = 5; // 에러! ref는 바꿀 수 없어
    std::cout << ref << std::endl;
}
```

### 📌 클래스 멤버 함수에서
```cpp
class Person {
public:
    string name;
    void print() const {
        // name = "John"; // 에러! const 함수는 멤버 못 바꿈
        std::cout << name << std::endl;
    }
};
```

---

## 🎯 정리표

| 사용 위치 | 의미 | 예시 | 이유 |
|----------|------|------|------|
| 변수 앞 | 상수 선언 | `const int x = 10;` | 절대 안 바뀌는 값 |
| 함수 매개변수 | 입력만 받을 때 | `void f(const int x)` | 값 변경 방지 |
| 참조, 포인터 | 안전한 참조/포인터 | `const int* p` | 메모리 보호 |
| 멤버 함수 | 읽기 전용 함수 | `void f() const` | 멤버 수정 방지 |
