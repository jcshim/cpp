# 얕은 복사(shallow copy)와 깊은 복사(deep copy)

---

### 🎒 비유로 이해하기: “복사 가방 이야기”

#### 상황:
- 너한테는 연필, 지우개 등이 들어있는 **가방(포인터로 된 데이터)**이 있어.
- 누가 그 가방을 "복사"해달라고 해!

---

### 🧍‍♂️ 얕은 복사 (Shallow Copy)
> **가방 하나를 두 사람이 같이 씀**

- 겉보기엔 복사된 것처럼 보여도,  
- **안에 든 물건(데이터)은 같은 걸 같이 씀**
- 즉, 복사한 애가 안에 든 걸 바꾸면 원래 것도 같이 바뀜!

```cpp
class A {
public:
    int* data;
    A(int v) { data = new int(v); }            // 생성자
    A(const A& a) { data = a.data; }           // 얕은 복사
};
```

🧠 즉: **포인터 주소만 복사**함 (실제 내용은 공유)

---

### 🧍‍♂️🧍‍♀️ 깊은 복사 (Deep Copy)
> **가방도 따로, 안의 연필도 따로 복사**

- 완전한 사본을 만들어서, 서로 **간섭 없음!**
- 누가 바꿔도 서로 영향 X

```cpp
class A {
public:
    int* data;
    A(int v) { data = new int(v); }                // 생성자
    A(const A& a) { data = new int(*a.data); }     // 깊은 복사
};
```

🧠 즉: **새로운 메모리를 만들고, 내용까지 복사**함

---

### 💥 왜 중요할까?

- 얕은 복사는 빠르지만, 실수하면 **데이터 꼬임/중복 해제 오류** 발생!
- 깊은 복사는 안전하지만, **코드 더 쓰고 메모리 더 씀**

---

### 📌 핵심 한 줄 요약

- **얕은 복사**: 같은 걸 같이 씀 (주소만 복사)  
- **깊은 복사**: 완전한 사본 (내용까지 복사)

물론이죠! 얕은 복사와 깊은 복사의 차이를 보여주는 **아주 간단한 예제**를 드릴게요. 이해하기 쉬운 형태로 설명도 붙였어요.

---

### ✅ 얕은 복사 예제

```cpp
#include <iostream>
using namespace std;

class Shallow {
public:
    int* data;
    Shallow(int v) { data = new int(v); }
    Shallow(const Shallow& s) { data = s.data; } // 얕은 복사
    ~Shallow() { delete data; }
};

int main() {
    Shallow a(10);
    Shallow b = a;       // 얕은 복사 (주소만 복사)

    *b.data = 20;        // 하나 바꾸면 둘 다 바뀜
    cout << *a.data << endl; // 20 출력됨
}
```

🧨 **문제점**: `a`와 `b`가 같은 `data`를 가리켜서, 하나만 삭제해도 둘 다 영향받음. → **이중 삭제 에러 가능**

---

### ✅ 깊은 복사 예제

```cpp
#include <iostream>
using namespace std;

class Deep {
public:
    int* data;
    Deep(int v) { data = new int(v); }
    Deep(const Deep& d) { data = new int(*d.data); } // 깊은 복사
    ~Deep() { delete data; }
};

int main() {
    Deep a(10);
    Deep b = a;         // 깊은 복사 (내용까지 복사)

    *b.data = 20;       // 서로 독립
    cout << *a.data << endl; // 10 출력됨
}
```

✅ 안전하게 독립된 복사! `a`, `b`는 전혀 영향 안 줌.

---

필요하다면 더 짧게, 또는 실습 가능한 형태로도 줄여드릴 수 있어요!
