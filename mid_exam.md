### ✅ C++ 주관식 문항 제안 (사고 중심)
1. **C++에서 포인터와 참조의 차이를 간단히 설명하시오.**  
   *(개념 비교 + 실제 코드 적용 시기 판단)*

2. **다형성(polymorphism)이란 무엇이며, 이를 사용하는 이유를 간단한 예와 함께 설명하시오.**  
   *(객체지향 설계 사고 유도)*

3. **템플릿을 사용하는 이유를 한 문장으로 설명하고, 예를 들어 어떤 상황에서 유용할지 서술하시오.**  
   *(일반화 사고 + 추상화 능력 확인)*

4. **연산자 오버로딩이 왜 필요한지 설명하고, 오버로딩 시 주의할 점 한 가지를 적으시오.**  
   *(추상적 개념 + 실용적 제한사항 고려)*

5. **다음 중 가상 함수가 필요한 상황을 예로 들어 설명하시오. (예: 동물 클래스에서의 행동 정의 등)**  
   *(상속 구조와 실행 흐름 사고 유도)*
---

### ✅ 난이도 높은 C++ 코딩형 시험 문제 5선

---

**1. 연산자 오버로딩 – 복소수 클래스**  
> 실수부와 허수부를 가지는 `Complex` 클래스를 정의하고, `+` 연산자를 오버로딩하여 두 복소수를 더하는 프로그램을 작성하시오.  
> 결과는 `a+bi` 형태로 출력되어야 한다.

- 🔑출제 의도: 클래스 구현, 연산자 오버로딩, 출력 형식 구성

---

**2. 템플릿 클래스 – Stack 구현**  
> 템플릿 클래스를 이용하여 자료형에 상관없이 동작하는 `MyStack` 클래스를 작성하시오.  
> 주요 함수: `push()`, `pop()`, `top()`, `isEmpty()`  
> 메인 함수에서 `int`, `string` 두 자료형으로 각각 사용 예시를 보이시오.

- 🔑출제 의도: 클래스 템플릿 정의, 함수 구현, 예외 처리 또는 기본적 오류 방지

---

**3. 포인터와 소멸자 – 동적 배열 클래스 구현**  
> 정수형 동적 배열을 관리하는 `IntArray` 클래스를 구현하시오.  
> 요구사항: 생성자, 소멸자, 요소 추가 함수 `add(int)`, 배열 출력 함수 `print()`  
> (단, `new`와 `delete[]` 사용 필수)

- 🔑출제 의도: 동적 메모리 할당 및 해제, 소멸자 구현, 안전한 메모리 관리

---

**4. 상속과 가상 함수 – 다형성 설계**  
> `Shape` 클래스를 추상 클래스로 만들고, 이를 상속받는 `Rectangle`, `Circle` 클래스를 작성하시오.  
> 각각 `area()` 함수를 오버라이딩하고, 포인터 배열로 여러 도형의 넓이를 출력하시오.  

- 🔑출제 의도: 추상 클래스, 순수 가상 함수, 다형성, 동적 바인딩 이해

---

**5. STL 활용 – 학생 평균 점수 정렬**  
> `struct Student { string name; vector<int> scores; }`  
> 이름과 점수를 입력받아 평균 점수를 계산하고, 평균 기준으로 내림차순 정렬하여 출력하는 프로그램을 작성하시오.  
> (단, `sort()`, `lambda 표현식` 사용 필수)

- 🔑출제 의도: STL 알고리즘 활용, 람다 함수, 구조체 정렬

## **최소한의 표현으로 명확하게 요약한 정답**

---

### 1. **포인터 vs 참조 (개념 + 적용 시기)**  
- **포인터**는 주소를 저장하는 변수로 `null` 가능, **참조**는 변수의 별칭으로 반드시 초기화 필요.  
- 동적 메모리 관리나 `nullptr` 처리 필요 시 포인터 사용, 객체 전달 및 불변성이 요구될 때 참조 사용.

---

### 2. **다형성(polymorphism)이란? (개념 + 이유 + 예)**  
- **다형성**은 동일한 인터페이스로 다양한 객체의 동작을 실행하는 것.  
- 유지보수성과 확장성 향상.  
  예) `Animal* a = new Dog();` → `a->speak();` 실행 시 실제 객체에 따라 다른 함수 호출됨.

---

### 3. **템플릿의 목적과 활용 상황 (일반화 + 추상화)**  
- 템플릿은 **자료형에 독립적인 재사용 가능한 코드를 작성**하기 위해 사용된다.  
- 예: `MyStack<T>`를 구현하면 `int`, `string`, 사용자 정의 타입 모두 동일 구조로 사용 가능.

---

### 4. **연산자 오버로딩의 필요성과 주의점 (개념 + 제한)**  
- 연산자 오버로딩은 **사용자 정의 타입에 자연스러운 연산 표현**을 가능하게 한다.  
- **주의점**: 의미 없는 연산을 정의하거나 일관성 없는 동작을 구현하지 않도록 주의해야 함.

---

### 5. **가상 함수 필요 상황 예시 (상속 + 실행 흐름)**  
- 부모 포인터로 자식 객체를 다룰 때, **자식의 메서드를 호출하려면 가상 함수가 필요**하다.  
- 예: `Animal` 클래스의 `sound()`를 `virtual`로 선언 → `Dog`, `Cat`의 각기 다른 소리를 실행.

## 코딩 답안
아래는 C++에서 `Complex` 클래스를 정의하고 `+` 연산자를 오버로딩하여 두 복소수를 더한 후, `a+bi` 형식으로 출력하는 예제입니다:

```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    double real;  // 실수부
    double imag;  // 허수부

public:
    // 생성자
    Complex(double r = 0, double i = 0) : real(r), imag(i) {}

    // + 연산자 오버로딩
    Complex operator+(const Complex& other) const {
        return Complex(real + other.real, imag + other.imag);
    }

    // 출력 함수
    void display() const {
        cout << real << (imag >= 0 ? "+" : "") << imag << "i" << endl;
    }
};

int main() {
    Complex c1(3, 4);   // 3+4i
    Complex c2(1, -2);  // 1-2i

    Complex sum = c1 + c2;
    sum.display();  // 결과: 4+2i

    return 0;
}
```

✅ **핵심 포인트 요약**  
- 클래스 내부에 멤버 변수 `real`, `imag`를 선언  
- 생성자에서 기본값을 허용하여 초기화  
- `operator+` 함수로 복소수 덧셈 정의  
- 출력 시 `+`와 `-`를 적절히 구분하여 `a+bi` 형태로 출력  

필요 시 `<<` 연산자도 오버로딩해드릴 수 있어요.

아래는 C++ 템플릿을 이용한 `MyStack` 클래스 구현 예제입니다. `int`와 `string` 자료형에 대해 사용 예시도 포함되어 있습니다.

```cpp
#include <iostream>
#include <vector>
#include <string>
using namespace std;

template <typename T>
class MyStack {
private:
    vector<T> data;

public:
    void push(const T& value) {
        data.push_back(value);
    }

    void pop() {
        if (!isEmpty()) {
            data.pop_back();
        } else {
            cout << "스택이 비어 있어 pop 할 수 없습니다." << endl;
        }
    }

    T top() const {
        if (!isEmpty()) {
            return data.back();
        } else {
            throw out_of_range("스택이 비어 있습니다.");
        }
    }

    bool isEmpty() const {
        return data.empty();
    }
};

// 사용 예시
int main() {
    MyStack<int> intStack;
    intStack.push(10);
    intStack.push(20);
    cout << "intStack top: " << intStack.top() << endl;
    intStack.pop();
    cout << "intStack top after pop: " << intStack.top() << endl;

    MyStack<string> stringStack;
    stringStack.push("Hello");
    stringStack.push("World");
    cout << "stringStack top: " << stringStack.top() << endl;
    stringStack.pop();
    cout << "stringStack top after pop: " << stringStack.top() << endl;

    return 0;
}
```

✅ **핵심 포인트 요약**  
- `template <typename T>`를 사용해 자료형에 관계없이 동작하는 스택 정의  
- 내부 저장소로 `vector<T>` 사용  
- `push()`, `pop()`, `top()`, `isEmpty()` 함수 구현  
- 예외 상황에 대한 최소한의 오류 방지 또는 안내 메시지 처리  

원하면 `try-catch` 구조를 활용해 예외를 잡는 예제도 추가해줄 수 있어요.

다음은 `new`와 `delete[]`를 이용하여 정수형 동적 배열을 관리하는 `IntArray` 클래스 예제입니다. 요소 추가 시 배열을 동적으로 재할당하며, 소멸자를 통해 메모리 누수를 방지합니다.

```cpp
#include <iostream>
using namespace std;

class IntArray {
private:
    int* data;
    int size;
    int capacity;

    // 배열 크기 확장 함수
    void resize() {
        capacity *= 2;
        int* newData = new int[capacity];
        for (int i = 0; i < size; ++i)
            newData[i] = data[i];
        delete[] data;
        data = newData;
    }

public:
    // 생성자
    IntArray(int initialCapacity = 2) : size(0), capacity(initialCapacity) {
        data = new int[capacity];
    }

    // 소멸자
    ~IntArray() {
        delete[] data;
    }

    // 요소 추가
    void add(int value) {
        if (size == capacity) {
            resize();
        }
        data[size++] = value;
    }

    // 배열 출력
    void print() const {
        for (int i = 0; i < size; ++i) {
            cout << data[i] << " ";
        }
        cout << endl;
    }
};

// 사용 예시
int main() {
    IntArray arr;
    arr.add(5);
    arr.add(10);
    arr.add(15);  // resize() 발생
    arr.print();  // 출력: 5 10 15

    return 0;
}
```

✅ **핵심 포인트 요약**  
- 생성자에서 `new int[]`로 메모리 할당  
- 소멸자에서 `delete[]`로 안전하게 해제  
- `add()`에서 필요 시 `resize()` 호출로 용량 2배 증가  
- `print()`로 요소 출력  

원하면 `복사 생성자`와 `대입 연산자 오버로딩`도 추가해줄 수 있어요 (Rule of Three).

다음은 `Shape` 클래스를 추상 클래스로 정의하고, 이를 상속한 `Rectangle`과 `Circle` 클래스에서 `area()` 함수를 오버라이딩하는 예제입니다. 포인터 배열을 통해 다형성을 활용하여 여러 도형의 넓이를 출력합니다.

```cpp
#include <iostream>
#include <cmath>
using namespace std;

// 추상 클래스
class Shape {
public:
    virtual double area() const = 0; // 순수 가상 함수
    virtual ~Shape() {}              // 가상 소멸자
};

// 사각형 클래스
class Rectangle : public Shape {
private:
    double width, height;
public:
    Rectangle(double w, double h) : width(w), height(h) {}
    double area() const override {
        return width * height;
    }
};

// 원 클래스
class Circle : public Shape {
private:
    double radius;
public:
    Circle(double r) : radius(r) {}
    double area() const override {
        return M_PI * radius * radius;
    }
};

int main() {
    Shape* shapes[3];
    shapes[0] = new Rectangle(3, 4); // 넓이: 12
    shapes[1] = new Circle(2);       // 넓이: 약 12.57
    shapes[2] = new Rectangle(5, 2); // 넓이: 10

    for (int i = 0; i < 3; ++i) {
        cout << "도형 " << i + 1 << "의 넓이: " << shapes[i]->area() << endl;
        delete shapes[i]; // 메모리 해제
    }

    return 0;
}
```

✅ **핵심 포인트 요약**  
- `Shape` 클래스는 `area()`를 순수 가상 함수로 선언하여 추상 클래스가 됨  
- `Rectangle`, `Circle` 클래스는 `area()`를 오버라이딩  
- 포인터 배열을 통해 다형성(dynamic binding) 구현  
- 소멸자는 가상 함수로 선언하여 리소스 누수 방지  

필요 시 `vector<Shape*>`로도 구현 가능하며, 더 많은 도형 확장도 가능합니다.

아래는 `struct Student`와 `STL vector`, `sort()`, `lambda`를 이용하여 학생의 평균 점수를 계산하고, 내림차순 정렬하여 출력하는 예제입니다.

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

struct Student {
    string name;
    vector<int> scores;

    // 평균 점수 계산 함수
    double average() const {
        if (scores.empty()) return 0;
        int sum = 0;
        for (int s : scores) sum += s;
        return static_cast<double>(sum) / scores.size();
    }
};

int main() {
    vector<Student> students = {
        {"Alice", {90, 80, 70}},
        {"Bob", {100, 85}},
        {"Charlie", {75, 85, 80, 90}}
    };

    // 평균 기준 내림차순 정렬
    sort(students.begin(), students.end(), [](const Student& a, const Student& b) {
        return a.average() > b.average();
    });

    // 출력
    for (const auto& s : students) {
        cout << s.name << " 평균: " << s.average() << endl;
    }

    return 0;
}
```

✅ **핵심 포인트 요약**  
- `struct Student`에 이름과 점수 목록 저장  
- `average()` 함수로 평균 점수 계산  
- `sort()`와 `lambda`로 평균 기준 내림차순 정렬  
- `vector<Student>`로 유연한 학생 리스트 처리  

💡 *학생 수나 점수를 사용자로부터 입력받도록 확장도 가능하며, `cin`과 루프를 활용하면 됩니다.*
