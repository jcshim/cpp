**C++의 객체지향 프로그래밍(OOP)** 개념 중에서 **추상 클래스**, **순수 가상 함수**, **다형성(polymorphism)** 등을 보여주는 예제

---

### 1. `Animal` 클래스

```cpp
class Animal {
public:
    virtual void sound() = 0; // 순수 가상 함수
};
```

- `Animal`은 **추상 클래스**입니다.  
- `sound()`라는 **순수 가상 함수**(pure virtual function)를 가지고 있습니다.
  - `= 0`이라는 문법은 "이 함수는 정의하지 않고, 자식 클래스에서 반드시 재정의(override)해야 한다"는 의미입니다.
- 이 때문에 `Animal` 클래스는 직접 객체로 만들 수 없습니다.

---

### 2. `Cat` 클래스와 `Dog` 클래스

```cpp
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
```

- `Cat`과 `Dog`는 `Animal` 클래스를 상속받은 **자식 클래스**입니다.
- `sound()` 함수를 오버라이딩(재정의)해서, 각각 고양이 소리("야옹")와 강아지 소리("멍멍")를 출력하게 했습니다.

---

### 3. `main()` 함수

```cpp
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

- `Animal* p`는 **기본 클래스 포인터**입니다.
- `p`를 통해 `Cat`과 `Dog` 객체를 번갈아 가리키고 있습니다.
- `p->sound();`는 실제로 어떤 객체를 가리키느냐에 따라 다르게 동작합니다.
  - `p = &c;`일 때는 `Cat::sound()`가 호출되어 "야옹"
  - `p = &d;`일 때는 `Dog::sound()`가 호출되어 "멍멍"

### 👉 이게 바로 **다형성(polymorphism)** 입니다.
> "하나의 포인터(`p`)가 다양한 형태(`Cat`, `Dog`)의 객체를 다룰 수 있다"는 개념이죠.

---

### 🔑 정리

| 요소         | 의미                                                  |
|--------------|--------------------------------------------------------|
| `virtual`    | 가상 함수로 선언 (런타임 시점에 어떤 함수 호출할지 결정) |
| `= 0`        | 순수 가상 함수 → 이 클래스를 추상 클래스로 만듬         |
| `override`   | 부모 클래스의 가상 함수를 재정의했다는 것을 명시        |
| 다형성       | 하나의 부모 포인터로 여러 자식 객체를 제어 가능         |

---
