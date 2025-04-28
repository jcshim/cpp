# ✅ C++ 다형성(polymorphism) 관련 키워드 정리

## [ 기본 개념 ]
- **polymorphism**  
  → 같은 인터페이스(함수 호출)로 다양한 동작(구현)을 수행하는 객체지향 개념.

- **dynamic polymorphism**  
  → 실행 시간(runtime) 결정되는 다형성 (가상 함수 기반).

- **static polymorphism**  
  → 컴파일 시간(compile time) 결정되는 다형성 (템플릿/오버로딩 기반).

---

## [ 동적 다형성 (Dynamic Polymorphism) 키워드 ]

- **virtual**  
  → 부모 클래스 함수가 자식 클래스에서 재정의(override)될 수 있도록 지정하는 키워드.

- **override**  
  → 자식 클래스가 부모 클래스의 가상 함수를 정확히 재정의했음을 명시하는 키워드(C++11 이후).

- **final**  
  → 더 이상 가상 함수 재정의를 막거나 클래스를 상속 불가능하게 만드는 키워드(C++11 이후).

- **pure virtual function**  
  → `= 0`으로 선언하여 반드시 파생 클래스에서 구현해야 하는 함수(추상 메서드).

- **abstract class**  
  → 하나 이상의 순수 가상 함수를 가지는 클래스 (객체 생성 불가).

- **base class pointer/reference**  
  → 부모 클래스 타입 포인터(또는 참조)로 자식 클래스 객체를 조작하는 것 (다형성 핵심).

---

## [ 정적 다형성 (Static Polymorphism) 키워드 ]

- **function overloading**  
  → 같은 이름의 함수를 매개변수 타입/개수에 따라 여러 개 정의하는 것.

- **operator overloading**  
  → 연산자(`+`, `-`, `*`, `==` 등)를 사용자 정의 타입에 맞게 재정의하는 것.

- **template**  
  → 자료형에 상관없이 같은 코드 구조를 여러 타입에 대해 동작하도록 만드는 문법.

- **class template**  
  → 여러 자료형에 대해 공통 동작을 수행할 수 있도록 일반화된 클래스 정의.

---

## [ 기타 다형성 관련 키워드 ]

- **dynamic_cast**  
  → 런타임에 타입 안전성을 검사하면서 다운캐스팅(부모 → 자식)하는 연산자.

- **typeid**  
  → 런타임에 객체의 실제 타입(type information)을 얻는 연산자.

- **RTTI (Run-Time Type Information)**  
  → 실행 중 객체의 타입 정보를 제공하는 시스템 (dynamic_cast, typeid 관련).

---

# ✨ 요약
- **동적 다형성** : `virtual`, `override`, `pure virtual function`, `dynamic_cast`
- **정적 다형성** : `overloading`, `templates`
- **기타** : `typeid`, `RTTI`

---
  
필요하시면 추가로,  
👉 **"C++ 다형성 키워드별 예제 코드 모음"**  
👉 **"시험 대비용 초간단 1장 요약"**  
👉 **"초보자용 다형성 실습 프로젝트 예제"**  
도 만들어드릴 수 있습니다!

추가로 원하시나요? 🚀  
(예: `virtual`과 `override` 예제 코드 같이)
