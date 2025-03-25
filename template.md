### 정수와 실수를 메모리에 초기화하고 더하기 int a = 10;
```
#include <iostream>
int main() {
    int a1=2, a2=3;
    std::cout << a1 + a2 << '\n';
    double f1(2.2), f2(3.3);
    std::cout << f1 + f2 << '\n';
}
```
### 정수와 실수를 메모리에 초기화하고 더하기 int a(10);
```
#include <iostream>
int main() {
    int a1(2), a2(3);
    std::cout << a1 + a2 << '\n';
    double f1(2.2), f2(3.3);
    std::cout << f1 + f2 << '\n';
}
```
### 두 수를 함수를 이용하여 더하기
```
int Add1(int a, int b){
	return a + b;
}
double Add2(double a, double b){
	return a + b;
}
int main() {
    int a1(2), a2(3);
    std::cout << Add1(a1, a2) << '\n';
    double f1(2.2), f2(3.3);
    std::cout << Add2(f1, f2) << '\n';
}
```
### 함수의 오버로딩 overloading: 매개변수의 형태나 갯수로 구분
```
int Add(int a, int b){
	return a + b;
}
double Add(double a, double b){
	return a + b;
}
int main() {
    int a1(2), a2(3);
    //short int 
    //long int
    // unsinged int
    // unsinged long int
    // float
    // ......
    std::cout << Add(a1, a2) << '\n';
    double f1(2.2), f2(3.3);
    std::cout << Add(f1, f2) << '\n';
}
```
### 함수의 템플릿
```
template <typename T>
T Add(T a, T b){
	return a + b;
}
int main() {
    int a1(2), a2(3);
    std::cout << Add(a1, a2) << '\n';
    double f1(2.2), f2(3.3);
    std::cout << Add(f1, f2) << '\n';
}
```
