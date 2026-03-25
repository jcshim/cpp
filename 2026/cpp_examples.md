C++의 강력한 기능(객체지향, 메모리 관리, 현대적 문법, 성능 최적화)을 한 번에 보여주기에 가장 좋은 예제는 **"스마트 포인터를 이용한 도형 관리 시스템"**입니다. 

이 예제 하나에 **상속, 다형성, 초기화 리스트, 가상 함수, 스마트 포인터, 람다, constexpr, RAII** 등 오늘 논의한 거의 모든 핵심 요소를 녹여낼 수 있습니다.

---

### 🚀 현대적 C++ 종합 선물 세트 예제

이 코드는 `CPoly`라는 부모 클래스를 상속받는 여러 도형을 `vector`와 `스마트 포인터`로 관리하며, `람다`를 이용해 일괄 처리하는 구조입니다.

```cpp
#include <iostream>
#include <vector>
#include <memory>   // 스마트 포인터 (unique_ptr)
#include <algorithm> // for_each

using namespace std;

// 1. 추상 기반 클래스 (RAII & 다형성 & 추상화)
class CPoly {
protected:
    int wid, hig;
public:
    // 멤버 초기화 리스트 & constexpr 생성자
    constexpr CPoly(int w, int h) : wid(w), hig(h) {}

    // 가상 소멸자 (상속 구조에서 필수!)
    virtual ~CPoly() { cout << "도형 메모리 해제" << endl; }

    // 순수 가상 함수 (인터페이스 강제)
    virtual void Area() const = 0; 
};

// 2. 자식 클래스: 사각형 (상속 & 오버라이딩)
class CRect : public CPoly {
public:
    using CPoly::CPoly; // 부모 생성자 상속 (C++11)
    
    void Area() const override {
        cout << "[사각형] 면적: " << wid * hig << endl;
    }
};

// 3. 자식 클래스: 삼각형 (상속 & 오버라이딩)
class CTri : public CPoly {
public:
    using CPoly::CPoly;

    void Area() const override {
        cout << "[삼각형] 면적: " << (wid * hig) / 2.0 << endl;
    }
};

int main() {
    // 4. 스마트 포인터와 벡터 (자동 메모리 관리)
    // unique_ptr를 담는 벡터를 생성하여 malloc/free 없이 자원 관리
    vector<unique_ptr<CPoly>> shapes;

    // 5. 객체 추가 (make_unique 활용)
    shapes.push_back(make_unique<CRect>(10, 20));
    shapes.push_back(make_unique<CTri>(10, 20));

    cout << "--- 모든 도형의 면적 계산 ---" << endl;

    // 6. 람다 표현식 (간결한 순회 및 콜백)
    // [&] 캡처를 통해 주변 객체에 접근하고, 다형성을 통해 Area 호출
    for_each(shapes.begin(), shapes.end(), [](const auto& s) {
        if (s != nullptr) { // nullptr 체크
            s->Area(); 
        }
    });

    return 0; // 7. 함수 종료 시 shapes가 파괴되면서 모든 도형 자동 delete (RAII)
}
```

---

### 🛠️ 이 예제에 포함된 C++ 핵심 기능들

| 번호 | 기능명 | 코드 내 적용 부분 |
| :--- | :--- | :--- |
| **1** | **추상화/상속** | `class CRect : public CPoly` (공통 속성 물려받기) |
| **2** | **다형성** | `virtual void Area() = 0` (실행 시점에 함수 결정) |
| **3** | **가상 소멸자** | `virtual ~CPoly()` (부모 포인터 삭제 시 자식 소멸 방지) |
| **4** | **스마트 포인터** | `unique_ptr`, `make_unique` (수동 `delete` 제거) |
| **5** | **람다(Lambda)** | `[](const auto& s) { ... }` (익명 함수 활용) |
| **6** | **초기화 리스트** | `: wid(w), hig(h)` (효율적인 초기화) |
| **7** | **STL 컨테이너** | `vector<unique_ptr<CPoly>>` (동적 배열 관리) |
| **8** | **상수성(const)** | `void Area() const` (멤버 변수 수정 방지 안정성) |



이 코드를 직접 컴파일해서 실행해 보시면, 현대 C++이 얼마나 강력하고 안전하게 자원을 관리하는지 한눈에 체감하실 수 있습니다. 

혹시 이 예제에 **템플릿(Template)**을 추가해서 어떤 자료형(float, double 등)이든 계산할 수 있게 업그레이드해 볼까요? 도와드릴 준비가 되어 있습니다!
