```
#include <iostream>
#include <memory>  // 스마트 포인터 사용을 위한 헤더
using namespace std;

class CPnt {
private:
    int x, y;
public:
    CPnt(int x = 0, int y = 0) : x(x), y(y) {}
    void display() const {
        cout << "(" << x << ", " << y << ")" << endl;
    }
};

int main() {
    unique_ptr<CPnt> p1 = make_unique<CPnt>(1, 1);  // 스마트 포인터 사용
    p1->display();  // -> 연산자로 접근

    return 0;
}
```
