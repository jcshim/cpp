# **분야별로만 정리**

### 🔹 기본 개념
- variable  
- function  
- member variable  
- member function  

---

### 🔹 클래스와 객체 관련
- class  
- object  
- object variable  
- object pointer  
- new  
- delete  

---

### 🔹 생성자 관련
- constructor  
- constructor overloading  
- constructor initialize  
- default constructor  
- copy constructor  
- move constructor  
- constructor delegation  

---

### 🔹 접근 지정자 및 참조
- private  
- public  
- & (reference operator)  
- reference  
- const  

---

### 🔹 함수 매개변수 방식
- `void foo(CPnt p)`  
- `void foo(CPnt& p)`  
- `void foo(const CPnt& p)`  

---

### 🔹 연산자 및 입출력
- friend  
- operator +  
- ostream, <<  
- istream, >>  

---

### 🔹 객체지향 확장 개념
- inheritance  
- overriding  
- virtual function  
- override keyword  
- polymorphism  
- abstract class  

---

### 🔹 현대 C++ / 고급 문법
- lambda function  
- template  
- smart pointer  
- dynamic allocation

#  C++의 개념들을 **초급**, **중급**, **고급**으로 나누어 정리

## ✅ 초급 (기초 문법과 객체지향 기본)

**🔹 기본 문법**
- variable  
- function  
- reference (&)  
- const  
- typedef / using  
- namespace  
- preprocessor (`#include`, `#define`)  

**🔹 조건문 및 반복문**
- if / else  
- switch  
- for / while / do-while  
- break / continue  

**🔹 함수 기초**
- 함수 정의 및 호출  
- 함수 매개변수 (값 전달, 참조 전달)  
- default parameter  
- function overloading  

**🔹 클래스 기본**
- class  
- object  
- member variable  
- member function  
- access specifier: public / private  
- constructor / default constructor  
- constructor initialize  
- destructor  

**🔹 연산자 오버로딩 기초**
- operator +  
- friend  
- ostream, <<  
- istream, >>  

---

## ✅ 중급 (객체지향 심화 및 템플릿, STL 활용)

**🔹 객체지향 프로그래밍**
- inheritance  
- protected  
- overriding  
- virtual function  
- polymorphism  
- virtual destructor  
- abstract class (pure virtual function)  
- interface  

**🔹 생성자 심화**
- constructor overloading  
- copy constructor  
- constructor delegation  

**🔹 포인터 관련**
- object pointer  
- dynamic allocation (`new`, `delete`)  
- this pointer  

**🔹 템플릿**
- function template  
- class template  
- template specialization  

**🔹 STL (Standard Template Library)**
- vector  
- list  
- map / set  
- stack / queue  
- iterator  
- algorithm (`sort`, `find`, `count`)  
- range-based for  
- lambda function with STL  

**🔹 기타 문법**
- static member variable / function  
- enum class  
- function pointer  
- default member initialization  

---

## ✅ 고급 (현대 C++ 및 고급 제어)

**🔹 현대 C++ (C++11 ~ C++20)**
- auto  
- decltype  
- nullptr  
- move semantics (`std::move`, `std::forward`)  
- smart pointer (`unique_ptr`, `shared_ptr`)  
- initializer_list  
- uniform initialization (`{}` 초기화)  
- constexpr  
- structured bindings  
- std::function  
- std::bind  

**🔹 템플릿 고급**
- template metaprogramming  
- SFINAE (Substitution Failure Is Not An Error)  
- concepts (C++20)  

**🔹 예외 처리**
- try / catch / throw  
- standard exception classes (`std::exception`, `runtime_error` 등)  

**🔹 형변환 및 타입 정보**
- static_cast  
- dynamic_cast  
- const_cast  
- reinterpret_cast  
- typeid  

**🔹 다중 상속**
- multiple inheritance  
- diamond problem  
- virtual base class  
