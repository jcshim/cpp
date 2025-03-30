# static 변수

### ✅ 1. **함수 안에서 static 변수**
```cpp
void countCalls() {
    static int count = 0;
    count++;
    std::cout << count << std::endl;
}
```

#### 💡 왜 필요할까?
- `static` 없으면 함수가 호출될 때마다 `count`가 **초기화됨**.
- `static` 붙이면 함수가 몇 번 호출됐는지 **기억할 수 있음**.
- 즉, **값이 유지되는 지역 변수**가 됨!

---

### ✅ 2. **클래스 내부에서 static 멤버 변수/함수**
```cpp
class MyClass {
public:
    static int count;
    static void printCount() {
        std::cout << count << std::endl;
    }
};

int MyClass::count = 0;
```

#### 💡 왜 필요할까?
- 모든 객체가 공유해야 하는 값이 있을 때.
- 객체를 만들지 않아도 접근 가능.
- 예: 전체 객체 수를 세는 변수, 설정값, 공용 함수 등.

---

### ✅ 3. **파일 내에서 static 전역 변수/함수**
```cpp
// file1.cpp
static int hiddenValue = 10;

static void helper() {
    std::cout << "I'm only visible in this file!" << std::endl;
}
```

#### 💡 왜 필요할까?
- **다른 파일에서 접근 못하게 하기 위해서**!
- `static`을 쓰면 해당 변수나 함수는 **해당 소스파일에서만 사용 가능**함 (링크 단위 제한).

---

### 🎯 정리
| 사용 위치 | 의미 | 이유 |
|----------|------|------|
| 함수 안 | 값이 유지되는 지역 변수 | 함수 호출 간 값 유지 |
| 클래스 | 객체 간 공유 멤버 | 공통 데이터/기능 저장 |
| 파일 수준 | 외부 접근 제한 | 파일 내부 전용 처리 |
