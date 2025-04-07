
## 🔶 고급 개념 (CPnt 기반 확장)

### 1. **Inheritance (상속)**  
부모 클래스 CPnt를 상속받아 색상 정보를 추가한 ColoredPnt 클래스

```cpp
class CPnt {
protected:
    int x, y;
public:
    CPnt(int x = 0, int y = 0) : x(x), y(y) {}
    virtual void display() const {
        cout << "(" << x << ", " << y << ")";
    }
};

class ColoredPnt : public CPnt {
private:
    string color;
public:
    ColoredPnt(int x, int y, string color) : CPnt(x, y), color(color) {}

    void display() const override {  // 오버라이딩
        cout << color << " point: ";
        CPnt::display();
        cout << endl;
    }
};
```

### 2. **Overriding (오버라이딩)**  
부모의 `display()`를 자식 클래스에서 재정의 (위 예제에서 사용)

---

### 3. **Lambda Function (람다 함수)**  
객체 목록을 좌표 기준으로 정렬할 때 활용

```cpp
#include <vector>
#include <algorithm>

int main() {
    vector<CPnt> points = { CPnt(3,4), CPnt(1,2), CPnt(5,1) };

    sort(points.begin(), points.end(), [](const CPnt& a, const CPnt& b) {
        return a.getX() < b.getX();  // x 기준 오름차순
    });

    for (const auto& p : points)
        p.display();
}
```

> ※ `getX()` 함수는 `CPnt` 클래스에 `int getX() const { return x; }`로 정의되어 있어야 합니다.

---

### 4. **Template (템플릿)**  
다양한 자료형으로 CPnt 객체를 만들 수 있는 템플릿 클래스

```cpp
template<typename T>
class CPntT {
private:
    T x, y;
public:
    CPntT(T x = 0, T y = 0) : x(x), y(y) {}

    void display() const {
        cout << "(" << x << ", " << y << ")" << endl;
    }
};
```

```cpp
int main() {
    CPntT<int> p1(1, 2);
    CPntT<float> p2(1.5f, 2.3f);

    p1.display();  // (1, 2)
    p2.display();  // (1.5, 2.3)
}
```

---

## 🔹 보너스: 스마트 포인터 적용 (현대 C++ 스타일)

```cpp
#include <memory>

int main() {
    unique_ptr<CPnt> p = make_unique<CPnt>(3, 4);
    p->display();
}
```
