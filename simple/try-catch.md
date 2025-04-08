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
