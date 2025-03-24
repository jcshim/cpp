### 연산자 오버로딩 수업 자료

#### 정의: 사용자가 기존 연산자의 동작을 재정의하는 기능
#### 재정의 못하는 연산자: sizeof, typeid, Scope Resolution 연산자 (::), Class Member Access 연산자 (.), Member Pointer Access 연산자 (.*), Ternary 또는 Conditional 연산자 (?:).

1. x, y 멤버로 지점을 나타내는 클래스 CPnt를 정의하시오.
1) 생성자를 활용하여 초기화 하시오.
2) Out() 함수는 x, y를 출력한다.
2. 두 지점  CPnt p1(1,1), p2(2,2); 을 더한 p3의 위치를 구하는 Add() 함수를 구현하시오.
3. 연산자 +를 오버로딩하시오.

```
#include <iostream>
class CPnt{
    
};
int main() {
    CPnt p1(1,1);
    p1.Out();
    return 0;
}
```

```
#include <iostream>
class CPnt{
    int x, y;
public:
    CPnt(int _x=0, int _y=0):x(_x),y(_y){}
    void Out(){
        std::cout << x <<' '<< y << '\n';
    }
};
int main() {
    CPnt p1(1,1);
    p1.Out();
    return 0;
}
```

```
#include <iostream>
class CPnt{
    int x, y;
};
int main() {
    CPnt p1(1,1), p2(2,2);
    CPnt p3 = p1.Add(p2);
    p3.Out();
    return 0;
}
```

```
#include <iostream>
class CPnt{
    int x, y;
public:
    CPnt(int _x=0, int _y=0):x(_x),y(_y){}
    CPnt Add(CPnt& p){
        return (CPnt(x + p.x, y + p.y));
    }    
    void Out(){
        std::cout << x <<' '<< y << '\n';
    }
};
int main() {
    CPnt p1(1,1), p2(2,2);
    CPnt p3 = p1.Add(p2);
    p3.Out();
    return 0;
}
```
