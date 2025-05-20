# static

---

## ✅ 1. **함수 내부의 static 변수**

* **초기화는 단 한 번만**, 이후 호출 시 **값이 유지됨**
* 함수 내에서 선언되지만 **정적 저장 영역(static storage)에 존재**

```cpp
void countUp() {
    static int count = 0;
    count++;
    std::cout << "Count: " << count << std::endl;
}

int main() {
    countUp();  // Count: 1
    countUp();  // Count: 2
    countUp();  // Count: 3
}
```

📌 **사용 이유**: 함수 호출 간에도 데이터를 유지해야 할 때 (ex. 카운터, 캐시 등)

---

## ✅ 2. **클래스의 static 멤버 변수**

* **모든 객체가 공유하는 변수**, 객체가 없어도 접근 가능
* 클래스 내부에 선언 → 클래스 외부에서 **정의 및 초기화** 필요

```cpp
class Student {
public:
    static int totalStudents;
    Student() { totalStudents++; }
};

int Student::totalStudents = 0;

int main() {
    Student a, b;
    std::cout << Student::totalStudents << std::endl;  // 출력: 2
}
```

📌 **사용 이유**: 모든 인스턴스에 공통적인 값 저장 (예: 객체 수, 설정값)

---

## ✅ 3. **클래스의 static 멤버 함수**

* **객체 없이 호출 가능**
* `this` 포인터가 없으므로 **멤버 변수에는 접근 불가**
* 오직 **static 멤버 변수** 또는 **전역 변수**만 접근 가능

```cpp
class Math {
public:
    static int add(int a, int b) {
        return a + b;
    }
};

int main() {
    std::cout << Math::add(3, 4) << std::endl;  // 출력: 7
}
```

📌 **사용 이유**: 객체 상태에 의존하지 않는 유틸리티 함수 구현

---

## ✅ 4. **파일 수준에서의 static (전역 변수/함수)**

* 해당 변수/함수는 **정의된 파일 내에서만 유효 (internal linkage)**
* 다른 파일에서 `extern`으로 접근 **불가**

```cpp
// file1.cpp
static int hiddenValue = 42;
static void secretFunc() {
    std::cout << "Only file1.cpp can use this." << std::endl;
}
```

📌 **사용 이유**: **모듈 내부 구현을 숨기기 위해**, 이름 충돌 방지

---

## ✅ 요약표

| 위치/용도               | 의미 및 효과                          |
| ------------------- | -------------------------------- |
| 함수 내 `static` 변수    | 함수 호출 간 값 유지, 단 한 번만 초기화         |
| 클래스의 `static` 멤버 변수 | 모든 객체가 공유, 클래스 외부에서 정의 필요        |
| 클래스의 `static` 멤버 함수 | 객체 없이 호출 가능, 비-static 멤버에는 접근 불가 |
| 파일 수준 전역 변수/함수      | 정의된 파일 내부에서만 접근 가능 (링크 제한)       |

---

원하시면 `static` 관련 **퀴즈**, **메모리 구조(Stack/Heap/Static)** 설명, 또는 `extern`, `constexpr`과의 차이도 비교해 드릴 수 있습니다.
