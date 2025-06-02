# cpp cast
## 🔹 1. `dynamic_cast` – 실행 시간에 타입 검사하는 안전한 다운캐스트

```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() { cout << "Animal sound\n"; }
};

class Dog : public Animal {
public:
    void sound() override { cout << "Bark\n"; }
};

int main() {
    Animal* a = new Dog();  // 업캐스트
    Dog* d = dynamic_cast<Dog*>(a);  // 다운캐스트 (성공)
    
    if (d) d->sound();  // 출력: Bark
    
    Animal* a2 = new Animal();
    Dog* d2 = dynamic_cast<Dog*>(a2);  // 실패 → nullptr 반환
    
    if (d2 == nullptr) cout << "변환 실패\n";  // 출력: 변환 실패
    return 0;
}
```

---

## 🔹 2. `static_cast` – 명시적이고 컴파일 시간에 검사하는 변환

```cpp
#include <iostream>
using namespace std;

int main() {
    double pi = 3.14;
    int n = static_cast<int>(pi);  // 소수점 잘림
    cout << n << endl;  // 출력: 3
    return 0;
}
```

---

## 🔹 3. `reinterpret_cast` – 포인터/비트 수준 저수준 변환

```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 65;
    char* ch = reinterpret_cast<char*>(&x);
    cout << *ch << endl;  // 출력: A (ASCII 65)
    return 0;
}
```

🛑 매우 저수준이고 위험할 수 있으므로 꼭 필요할 때만 사용합니다.

---

## 🔹 4. `const_cast` – `const` 속성 제거

```cpp
#include <iostream>
using namespace std;

void print(char* str) {
    cout << str << endl;
}

int main() {
    const char* msg = "Hello";
    print(const_cast<char*>(msg));  // const 제거하여 함수 인자 전달
    return 0;
}
```

⚠️ 원래 `msg`를 수정하지 않는다면 안전하지만, \*\*const를 제거한 후 값을 변경하면 정의되지 않은 동작(UB)\*\*이 발생할 수 있습니다.
