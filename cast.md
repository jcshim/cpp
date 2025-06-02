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

---
좋은 질문입니다!
아래에 `static_cast`가 **무엇인지**, **왜 쓰는지**, 그리고 **왜 이렇게 작동하는지**에 대해 설명드리겠습니다.

---

## 🔷 `static_cast`란?

`static_cast`는 **컴파일 타임에 타입을 명시적으로 변환**할 때 사용하는 C++의 형 변환 연산자입니다.
다음과 같은 특징이 있습니다:

* **명시적 변환**이므로 의도를 코드에 분명히 드러냄
* **안전성 검사**를 일부 수행함 (예: 서로 관련된 타입 간 변환)
* **컴파일 타임에 처리**됨
* **런타임 오버헤드가 없음**

---

## 🔶 예제를 다시 보면:

```cpp
double pi = 3.14;
int n = static_cast<int>(pi);  // 소수점 잘림
```

이 코드는:

1. `pi`는 `double` 타입 → 실수형 (부동소수점)
2. `static_cast<int>(pi)`는 **`pi`를 `int`형으로 강제 변환**합니다.
3. 이때 `3.14`는 소수점이 **버려지고** `3`만 남습니다.

---

## 🔸 왜 `static_cast`를 사용하는가?

1. **암시적 형 변환을 명시적으로 표현**하고 싶을 때
   → `int n = pi;` 도 되지만, `static_cast`를 쓰면 "의도적으로 변환한다"는 뜻을 코드에 드러냅니다.

2. **실수에서 정수로 변환 시 데이터 손실이 발생할 수 있음**
   → 컴파일러는 `static_cast`를 사용함으로써 이런 **의도된 손실**을 개발자가 **직접 책임지는 것**으로 간주합니다.

3. **더 안전하고 명확한 코드 작성**을 유도
   → 나중에 코드를 보는 사람(혹은 자신)이 "왜 형 변환을 했는가?"를 쉽게 이해할 수 있습니다.

---

## 🔹 결론

```cpp
int n = static_cast<int>(pi);
```

이 코드는 단순히 `pi`를 정수로 변환하는 것처럼 보여도,

* **의도적인 형 변환**이라는 신호를 컴파일러와 사람 모두에게 주고,
* **암시적 오류** 가능성을 줄이며,
* **코드의 명확성**을 높여줍니다.
