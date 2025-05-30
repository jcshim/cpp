### 🔹 기본 개념
```
#include <iostream>
using namespace std;

class CPnt {
private:
    int x, y;

public:
    // 생성자
    CPnt(int x = 0, int y = 0) : x(x), y(y) {}

    // + 연산자 오버로딩
    CPnt operator+(const CPnt& other) const {
        return CPnt(x + other.x, y + other.y);
    }

    // 출력 함수
    void display() const {
        cout << "(" << x << ", " << y << ")" << endl;
    }
};

int main() {
    CPnt p1(3, 4);
    CPnt p2(1, 2);
    CPnt p3 = p1 + p2;  // + 연산자 사용

    cout << "p1 + p2 = ";
    p3.display();

    return 0;
}
```

- **variable**  
  값을 저장하는 메모리 공간의 이름(예: `int x = 10;`에서 `x`).

- **function**  
  특정 작업을 수행하는 코드 블록으로, 호출되어 실행됨.

- **member variable**  
  클래스 내부에 선언된 변수로, 객체의 속성을 저장함.

- **member function**  
  클래스 내부에 정의된 함수로, 객체의 동작(행위)을 정의함.

---

### 🔹 클래스와 객체 관련

- **class**  
  객체를 만들기 위한 설계도; 변수와 함수의 집합.

- **object**  
  클래스를 기반으로 생성된 실제 인스턴스(실체).

- **object variable**  
  클래스로부터 만들어진 변수, 즉 객체 자체(예: `CPnt p;`).

- **object pointer**  
  객체를 가리키는 포인터(예: `CPnt* ptr = new CPnt();`).

- **new**  
  동적 메모리에서 객체를 생성하고 그 주소를 반환하는 연산자.

- **delete**  
  `new`로 할당한 동적 메모리를 해제하는 연산자.

---

### 🔹 생성자 관련

- **constructor**  
  객체 생성 시 자동 호출되는 함수로, 초기화를 담당함.

- **constructor overloading**  
  매개변수가 다른 여러 생성자를 정의하여 다양한 방식으로 객체 생성 가능.

- **constructor initialize**  
  생성자에서 멤버 변수를 `:` 뒤에 나열하여 초기화하는 방식.

---

### 🔹 접근 지정자 및 참조

- **private**  
  외부에서 접근할 수 없는 멤버(변수, 함수)를 지정함.

- **public**  
  외부에서도 접근 가능한 멤버를 지정함.

- **& , reference operator**  
  참조 연산자로 변수의 별칭(alias)을 만들거나 참조 인자를 나타냄.

---

### 🔹 함수 매개변수 방식

- `void foo(CPnt p){}`  
  객체를 **값으로 복사**하여 전달 (비효율적, 원본 변경 안됨).

- `void foo(CPnt& p){}`  
  객체를 **참조로 전달**하며, **원본 수정 가능**.

- `void foo(const CPnt& p){}`  
  객체를 **참조로 전달하되**, **수정은 불가능** (권장 방식).

---

### 🔹 기타 중요 개념

- **reference**  
  변수의 또 다른 이름(별칭); 주소를 통해 직접 접근.

- **const**  
  변수나 객체가 **변경되지 않도록 보호**하는 키워드.

- **friend**  
  클래스 외부에서 정의되었지만, 클래스의 private 멤버에 접근할 수 있는 함수 또는 클래스.

- **operator +**  
  `+` 연산자를 클래스에서 직접 정의하여 사용자 정의 타입끼리 덧셈 가능하게 함.

- **ostream , <<**  
  출력 스트림 객체(`cout` 등)와 출력 연산자 `<<`; 객체 정보를 출력할 때 사용.

- **istream , >>**  
  입력 스트림 객체(`cin` 등)와 입력 연산자 `>>`; 객체 정보를 입력받을 때 사용.

---

필요하면 각 항목에 대해 코드 예제도 추가해드릴 수 있어요. 더 궁금한 항목 있으신가요? 😊
