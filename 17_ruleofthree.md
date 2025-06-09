

# ✅ Rule of Three란?

클래스가 다음 세 가지 중 **하나라도 사용자 정의**해야 한다면, **나머지 둘도 반드시 사용자 정의**해야 한다는 규칙입니다:

| 항목         | 역할                                                       |
| ---------- | -------------------------------------------------------- |
| **복사 생성자** | 객체를 복사해 새 객체를 생성할 때 동작 (`MyClass(const MyClass& other)`) |
| **대입 연산자** | 이미 생성된 객체에 다른 객체를 복사 대입할 때 동작 (`operator=`)              |
| **소멸자**    | 객체가 소멸될 때 자원을 정리하는 함수 (`~MyClass()`)                     |

---

## 🧠 왜 중요한가?

* 이 셋 모두 \*\*동적 자원(예: `new`로 할당한 메모리)\*\*을 관리하는 데 관여합니다.
* C++ 컴파일러는 기본적으로 얕은 복사를 수행하므로, 포인터를 사용할 경우 자원 충돌, 이중 해제, 메모리 누수 등의 문제가 발생합니다.
* 따라서 **깊은 복사**, **자원 해제**, **자기대입 방지**를 위해 세 함수 모두 구현이 필요합니다.

---

## 🛠 예제 코드 (깊은 복사 포함)

```cpp
#include <iostream>
using namespace std;

class MyClass {
private:
    int* data;

public:
    // 생성자
    MyClass(int value) {
        data = new int(value);
        cout << "생성자 호출\n";
    }

    // 복사 생성자 (deep copy)
    MyClass(const MyClass& other) {
        data = new int(*other.data);
        cout << "복사 생성자 호출\n";
    }

    // 대입 연산자 (deep copy + 자기 대입 방지)
    MyClass& operator=(const MyClass& other) {
        if (this != &other) {
            delete data;
            data = new int(*other.data);
        }
        cout << "대입 연산자 호출\n";
        return *this;
    }

    // 소멸자
    ~MyClass() {
        delete data;
        cout << "소멸자 호출\n";
    }

    void print() {
        cout << "값: " << *data << endl;
    }
};

int main() {
    MyClass a(10);
    MyClass b = a;      // 복사 생성자 호출
    MyClass c(0);
    c = b;              // 대입 연산자 호출
    return 0;
}
```

---

## ✅ 요약

| 함수     | 자동 생성됨 | 자원 직접 관리 시 사용자 정의 필요 |
| ------ | ------ | -------------------- |
| 복사 생성자 | O      | O                    |
| 대입 연산자 | O      | O                    |
| 소멸자    | O      | O                    |

---

## 📌 참고: Rule of Five / Rule of Zero

* **Rule of Five**: C++11 이후 이동 생성자(move constructor), 이동 대입 연산자까지 포함해서 다섯 가지 모두 고려해야 함
* **Rule of Zero**: 자원 관리를 스마트 포인터 등에 위임하면, 위 함수들을 아예 정의할 필요 없음 (`std::vector`, `std::unique_ptr` 등 사용 시)
