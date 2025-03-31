# initializer_list
### 중괄호 `{}`로 묶인 값들의 집합을 간단하게 함수나 클래스에 넘겨줄 수 있게 해주는 STL 도구

---

### ✅ initializer_list란?

> `{1, 2, 3}` 같은 값을 함수나 객체에 넘길 수 있게 해주는 **특수한 타입**

C++11부터 도입된 기능으로, 여러 개 값을 편하게 한 번에 넘길 수 있게 도와줘요.

---

### 📌 예제 1: 함수에 여러 값을 넘길 때

```cpp
#include <iostream>
#include <initializer_list>
using namespace std;

void print(initializer_list<int> nums) {
    for (int n : nums) cout << n << ' ';
}

int main() {
    print({1, 2, 3, 4, 5});  // 출력: 1 2 3 4 5
}
```

- `{1, 2, 3, 4, 5}`는 `initializer_list<int>` 타입으로 함수에 들어감
- 반복문으로 간단히 순회 가능

---

### 📌 예제 2: 클래스 생성자에서 사용

```cpp
#include <iostream>
#include <vector>
#include <initializer_list>
using namespace std;

class MyVec {
    vector<int> v;
public:
    MyVec(initializer_list<int> list) : v(list) {}
    void show() {
        for (int n : v) cout << n << ' ';
    }
};

int main() {
    MyVec mv = {10, 20, 30};
    mv.show();  // 출력: 10 20 30
}
```

- `{10, 20, 30}`를 생성자에 넘기면 자동으로 `initializer_list<int>`로 처리됨

---

### 🎯 언제 쓰면 좋을까?

- 여러 값을 한 번에 넘기고 싶을 때
- 함수 인자가 몇 개인지 미리 모를 때
- STL 컨테이너와 자연스럽게 연결하고 싶을 때

---

### 📎 한 줄 요약

> `initializer_list`는 `{}`로 여러 값을 넘길 수 있게 해주는 C++의 편리한 기능!

---

더 알고 싶으면 `std::initializer_list` 내부 구현이나, 가변 인자 함수(`...`)와 비교도 해드릴 수 있어요!
