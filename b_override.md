```
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() = 0; // 순수 가상 함수
};

class Cat : public Animal {
public:
    void sound() override {
        cout << "야옹\n";
    }
};

class Dog : public Animal {
public:
    void sound() override {
        cout << "멍멍\n";
    }
};

int main() {
    Animal* p;
    
    Cat c;
    p = &c;
    p->sound();

    Dog d;
    p = &d;
    p->sound();

    return 0;
}
```
