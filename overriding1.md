### C++ 함수 오버라이딩(Overriding) 쉽게 설명!

#### **1. 오버라이딩이란?**
오버라이딩(Overriding)이란 **부모 클래스(Base Class)** 에서 제공한 함수의 기능을 **자식 클래스(Derived Class)** 에서 다시 정의하는 것!

✔ **같은 이름, 같은 매개변수, 다른 기능!**

#### **2. 오버라이딩 예제**
```cpp 삼각형과 사각형의 면적 계산
#include <iostream>
class CPoly{
protected:
    int h, w;
public:
    CPoly(int x, int y) : h(x), w(y) {}
};
class CTri : public CPoly {
public:
    CTri(int x, int y) : CPoly(x, y) {}
    void Area() {
        std::cout << (h * w / 2) << '\n';
    }
};
class CRect : public CPoly {
public:
    CRect(int x, int y) : CPoly(x, y) {}
    void Area() {
        std::cout << (h * w) << '\n';
    }
};
int main() {
    CTri t(1, 2);
    t.Area();
    CRect r(1, 2);
    r.Area();
    return 0;
}
```

```cpp
#include <iostream>
using namespace std;

class P {
protected:
    int h, w;
public:
    P(int x, int y) : h(x), w(y) {}
    virtual void A() = 0;
};

class T : public P {
public:
    T(int x, int y) : P(x, y) {}
    void A() override {
        cout << h * w / 2 << '\n';
    }
};

class R : public P {
public:
    R(int x, int y) : P(x, y) {}
    void A() override {
        cout << h * w << '\n';
    }
};

int main() {
    P* p1 = new T(1, 2);
    P* p2 = new R(1, 2);
    p1->A();
    p2->A();
    delete p1;
    delete p2;
    return 0;
}
```
```cpp
#include <iostream>
using namespace std;
class CAnimal {
public:
    virtual void Sound() { // virtual 키워드 사용
        cout << "동물이 소리를 냅니다!" << endl;
    }
    virtual ~CAnimal(){} 
};
class CDog : public CAnimal {
public:
    void Sound() override { // 부모의 sound()를 재정의
        cout << "멍멍!" << endl;
    }
};
class CCat : public CAnimal {
public:
    void Sound() override { // 부모의 sound()를 재정의
        cout << "야옹!" << endl;
    }
};

int main() {
    CAnimal* myPet = new CCat(); // 부모 타입의 포인터로 자식 객체 참조
    myPet->Sound(); // "야용!" 출력 (오버라이딩 된 함수 호출)
    delete myPet;
    CAnimal* myPet = new CDog(); // 부모 타입의 포인터로 자식 객체 참조
    myPet->Sound(); // "멍멍!" 출력 (오버라이딩 된 함수 호출)
    delete myPet;
    return 0;
}
```
🔹 **포인트 정리!**
- `virtual` 키워드를 부모 클래스의 함수 앞에 붙이면, 자식 클래스에서 오버라이딩 가능
- `override` 키워드를 자식 클래스의 함수 뒤에 붙이면 오버라이딩 확인 가능
- 부모 클래스 포인터(`Animal*`)를 사용해도 자식 클래스의 오버라이딩 된 함수가 호출됨! (다형성)

#### **3. 오버로딩(Overloading)과 차이점**
|  | 오버라이딩(Overriding) | 오버로딩(Overloading) |
|---|---|---|
| 정의 | 부모 함수 재정의 | 같은 이름의 함수를 여러 개 정의 |
| 상속 관계 | 필요함 (부모-자식 클래스) | 필요 없음 (같은 클래스 내에서) |
| 매개변수 | 동일해야 함 | 다르게 설정 가능 |

📌 **간단 비교 예제**
```cpp
class Example {
public:
    void func(int x) { cout << "int: " << x << endl; } // 오버로딩 1
    void func(double x) { cout << "double: " << x << endl; } // 오버로딩 2
};
```
👉 **이것은 오버로딩!**  
반면, 부모 클래스에서 제공한 함수를 자식 클래스에서 바꿔버리면 **오버라이딩!**

#### **4. 오버라이딩의 핵심 포인트**
✅ `virtual` 키워드를 부모 클래스의 함수 앞에 붙인다.  
✅ `override` 키워드를 붙이면 실수 방지 가능!  
✅ 부모 클래스의 포인터를 통해 자식 클래스의 함수가 호출됨 (다형성 활용).  

💡 **쉽게 기억하자!**  
📌 **오버라이딩 = "부모의 함수를 자식이 새로 만든다!"** 🚀
