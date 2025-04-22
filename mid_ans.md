
**[단답형]**  
1. 함수 오버로딩  
2. public  
3. 객체지향  
4. 템플릿  
5. STL  
6. 연산자 오버로딩  
7. 가상 함수  
8. 템플릿  
9. throw  
10. unique_ptr  
11. 4  

**[복수 선택형]**  
12. C, E  
13. B, E  
14. B, E  
15. A, B  

**[용어 설명]**  
16. 클래스/함수/변수에 대해 정적 할당 또는 공유를 의미  
17. 상수화하여 수정 불가를 의미  
18. 자료형에 독립적인 제네릭 프로그래밍 기능  
19. 다른 클래스가 private/protected 멤버에 접근 가능하도록 허용  
20. try-catch 블록으로 예외 상황을 처리하는 메커니즘  

**[부분 코딩]**  
21. `unique_ptr`, `make_unique`, `*p`  
22. `[=]() { return 11 + 22; }()`  

**[코딩1]**  
23.  
```cpp
#include <iostream>
class CRect {
public:
    int w, h;
    CRect(int width, int height) : w(width), h(height) {}
    int area() { return w * h; }
};
int main() {
    CRect rect(20, 30);
    std::cout << rect.area() << '\n';
    return 0;
}
```

24.  
```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual double area() = 0;
};

class Rectangle : public Shape {
    double w, h;
public:
    Rectangle(double width, double height) : w(width), h(height) {}
    double area() override { return w * h; }
};

class Triangle : public Shape {
    double w, h;
public:
    Triangle(double width, double height) : w(width), h(height) {}
    double area() override { return w * h / 2; }
};

int main() {
    Rectangle r(20, 30);
    Triangle t(20, 30);
    cout << r.area() << '\n';
    cout << t.area() << '\n';
    return 0;
}
```

### 25. `input.txt` 읽고 출력, 실패시 예외 발생
```cpp
#include <iostream>
#include <fstream>
#include <stdexcept>
using namespace std;

int main() {
    ifstream file("input.txt");
    if (!file) throw runtime_error("파일 열기 실패");

    string line;
    while (getline(file, line)) {
        cout << line << endl;
    }
    return 0;
}
```

---

### 26. `CPnt` 클래스 덧셈 연산자 오버로딩
```cpp
#include <iostream>
using namespace std;

class CPnt {
public:
    int x, y;
    CPnt(int a = 0, int b = 0) : x(a), y(b) {}

    CPnt operator+(const CPnt& other) const {
        return CPnt(x + other.x, y + other.y);
    }
};

int main() {
    CPnt p1(1, 2), p2(3, 4);
    CPnt p3 = p1 + p2;
    cout << p3.x << ", " << p3.y << endl;
    return 0;
}
```

---

### 27. `unique_ptr` 배열로 2차원 좌표 저장 및 출력
```cpp
#include <iostream>
#include <memory>
using namespace std;

struct Point {
    int x, y;
    Point(int a, int b) : x(a), y(b) {}
};

int main() {
    unique_ptr<Point[]> points(new Point[3] { {1,2}, {3,4}, {5,6} });

    for (int i = 0; i < 3; ++i)
        cout << points[i].x << ", " << points[i].y << endl;

    return 0;
}
```

