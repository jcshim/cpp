```
#include <iostream>
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
    try {
        CPnt* p1 = new CPnt(1, 1);
        p1->display();
        delete p1;
    }
    catch (...) {
        cout << "예외 발생!" << endl;
    }

    return 0;
}
```

```
#include <iostream>
#include <new>  // std::bad_alloc을 위해 필요
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
    try {
        CPnt* p1 = new CPnt(1, 1);
        p1->display();
        delete p1;  // 메모리 해제
    }
    catch (const bad_alloc& e) {
        cerr << "메모리 할당 실패: " << e.what() << endl;
    }
    catch (const exception& e) {
        cerr << "예외 발생: " << e.what() << endl;
    }

    return 0;
}
```
