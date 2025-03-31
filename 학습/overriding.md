### **C++ Overriding (재정의)**
**Overriding(재정의)**는 객체지향 프로그래밍(OOP)에서 **상속(Inheritance)**을 사용할 때, **기반 클래스(Base Class, 부모 클래스)**의 멤버 함수를 **파생 클래스(Derived Class, 자식 클래스)**에서 새롭게 정의하는 기법입니다. 

---

## **1. 함수 재정의(Overriding)란?**
- **기반 클래스(Base Class)**에서 정의한 **멤버 함수**를 **파생 클래스(Derived Class)**에서 다시 정의(재정의)하는 것
- **함수의 이름, 반환형, 매개변수 목록이 동일**해야 함
- 파생 클래스에서 **새로운 기능을 추가하거나, 기존 동작을 변경**할 수 있음

---

## **2. Overriding의 특징**
- **기반 클래스의 함수는 `virtual` 키워드**를 사용하여 선언해야 함
- 오버라이딩된 함수는 **동적 바인딩(Dynamic Binding)**을 통해 **실행 시점(Run-time)에 결정**됨 (다형성, Polymorphism)
- `override` 키워드를 사용하면 오버라이딩 여부를 명확하게 표현할 수 있음 (C++11부터 지원)
- `final` 키워드를 사용하면 더 이상의 오버라이딩을 금지할 수 있음

---

## **3. Overriding 예제**
### **(1) 기본적인 오버라이딩**
```cpp
#include <iostream>
using namespace std;

class Parent {
public:
    virtual void show() { // virtual 키워드 사용
        cout << "부모 클래스 show() 함수" << endl;
    }
};

class Child : public Parent {
public:
    void show() override { // 오버라이딩 (override 키워드 사용 가능)
        cout << "자식 클래스 show() 함수" << endl;
    }
};

int main() {
    Parent* p;  
    Child c;     
    p = &c;  // 부모 클래스 포인터에 자식 클래스 객체 저장

    p->show();  // 동적 바인딩: Child 클래스의 show()가 호출됨
    return 0;
}
```
### **출력 결과**
```
자식 클래스 show() 함수
```
➡ **`virtual` 키워드가 없으면, `Parent` 클래스의 `show()` 함수가 호출됩니다.**

---

### **(2) `final` 키워드로 오버라이딩 방지**
```cpp
class Base {
public:
    virtual void func() final { // 더 이상 오버라이딩할 수 없음
        cout << "Base::func()" << endl;
    }
};

class Derived : public Base {
public:
    // void func() override {  // 컴파일 오류 발생 (Base에서 final로 선언됨)
    //     cout << "Derived::func()" << endl;
    // }
};
```
➡ `final` 키워드가 선언된 `func()` 함수는 더 이상 파생 클래스에서 재정의할 수 없습니다.

---

### **(3) 생성자와 소멸자의 오버라이딩**
**소멸자(Destructor)는 반드시 가상 함수로 선언해야 함**
```cpp
class Base {
public:
    virtual ~Base() { // 가상 소멸자
        cout << "Base 소멸자 호출" << endl;
    }
};

class Derived : public Base {
public:
    ~Derived() {
        cout << "Derived 소멸자 호출" << endl;
    }
};

int main() {
    Base* p = new Derived();
    delete p; // Derived -> Base 순서대로 소멸됨
    return 0;
}
```
### **출력 결과**
```
Derived 소멸자 호출
Base 소멸자 호출
```
➡ **기반 클래스의 소멸자가 `virtual`이 아니면, 파생 클래스의 소멸자가 호출되지 않는 문제가 발생할 수 있음.**

---

### **(4) 함수 숨김(Name Hiding) 주의**
파생 클래스에서 같은 이름의 함수를 정의하면 **기반 클래스의 함수가 가려질 수 있음**.
```cpp
class Parent {
public:
    virtual void show(int x) { 
        cout << "Parent::show(int)" << endl;
    }
};

class Child : public Parent {
public:
    void show() { // 오버라이딩이 아니라 Parent의 show(int) 숨김
        cout << "Child::show()" << endl;
    }
};

int main() {
    Child c;
    c.show();    // Child::show() 호출
    // c.show(10); // 오류 발생 (Parent의 show(int)가 숨겨짐)
    return 0;
}
```
➡ `Parent` 클래스의 `show(int)` 함수가 `Child` 클래스에서 가려지므로, `c.show(10);` 호출 시 오류 발생.

➡ 해결 방법:
```cpp
class Child : public Parent {
public:
    using Parent::show; // 부모 클래스의 show(int) 상속
    void show() { 
        cout << "Child::show()" << endl;
    }
};
```

---

## **4. Overriding vs Overloading**
| 비교 항목 | **Overriding (재정의)** | **Overloading (오버로딩)** |
|-----------|----------------|----------------|
| 적용 대상 | 상속된 멤버 함수 | 동일 클래스 내의 함수 |
| 함수명 | 같아야 함 | 같아야 함 |
| 매개변수 목록 | **동일해야 함** | **다르게 정의 가능** |
| 반환형 | **동일해야 함** (C++11 이후 일부 예외) | 무관 |
| 키워드 | `virtual`, `override` 사용 가능 | 사용 안 함 |
| 다형성(Polymorphism) | **O** (런타임 동적 바인딩) | **X** (컴파일타임 정적 바인딩) |

### **Overloading 예제**
```cpp
class Sample {
public:
    void func() { cout << "func() 호출" << endl; }
    void func(int x) { cout << "func(int) 호출" << endl; }
};
```
➡ **Overriding과 다르게 매개변수 목록이 다르면 오버로딩이 됨.**

---

## **5. 정리**
✅ **Overriding(재정의)**
- 부모 클래스의 `virtual` 함수를 자식 클래스에서 다시 정의
- 반드시 **함수명, 반환형, 매개변수 목록이 동일해야 함**
- **다형성(Polymorphism) 지원**
- `override`, `final` 키워드를 사용하여 코드 안정성을 높일 수 있음
- 소멸자는 **반드시 `virtual`로 선언**해야 함 (메모리 누수 방지)

✅ **Overloading(오버로딩)과 혼동 주의**
- Overloading은 **매개변수 개수, 타입이 다를 때 적용**
- Overriding은 **상속 관계에서 부모 함수의 기능을 변경**하는 것

이해가 잘 되었나요? 😊 필요하면 더 자세한 설명이나 예제를 추가해 드릴 수 있습니다! 🚀
