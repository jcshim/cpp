정적 멤버 변수(static member variable)와 정적 멤버 함수(static member function)

---

### ✅ 정적 멤버 예제 (가장 단순한 형태)

```cpp
#include <iostream>
using namespace std;

class MyClass {
public:
    static int count;  // 정적 멤버 변수 선언

    MyClass() {
        count++;  // 객체가 생성될 때마다 count 증가
    }

    static void showCount() {  // 정적 멤버 함수
        cout << "총 객체 수: " << count << endl;
    }
};

// 정적 멤버 변수 정의 및 초기화
int MyClass::count = 0;

int main() {
    MyClass a;
    MyClass b;
    MyClass c;

    MyClass::showCount();  // 객체 없이 클래스 이름으로 호출

    return 0;
}
```

---

### 🧠 설명
- `static int count;` → 모든 객체가 **공유**하는 변수.
- `static void showCount();` → 객체 없이 호출 가능한 함수.
- `int MyClass::count = 0;` → 정적 멤버 변수는 **클래스 외부에서 초기화**해야 함.
- 출력 결과: `총 객체 수: 3`
