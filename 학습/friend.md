좋습니다! 이 코드는 `friend` 키워드를 **학생들이 직접 추가해보도록** 의도적으로 생략한 예제입니다. 하나씩 천천히 설명해드릴게요:

---

### 🔍 현재 코드 분석

```cpp
#include <iostream>

class CMy {
private:
    int a = 42;
public:
    // friend 함수 선언
       void Pr(CMy o);
};

// friend 함수 정의
void Pr(CMy o) {
    std::cout << o.a << '\n';  // ❗ 오류 발생 가능
}
```

---

### ⚠️ 현재 상태에서는 컴파일 에러가 발생함

- 이유: `Pr(CMy o)` 함수는 `CMy` 클래스 외부에 정의되어 있고, `private` 멤버인 `a`에 접근하려고 합니다.
- 하지만 `Pr` 함수는 **friend가 아니기 때문에** 클래스의 `private` 멤버에 접근할 **권한이 없습니다.**

---

### ✅ 수정 방법: `friend` 키워드 추가

학생들이 다음과 같이 직접 `friend` 키워드를 추가해줘야 합니다:

```cpp
class CMy {
private:
    int a = 42;
public:
    // friend 함수 선언
    friend void Pr(CMy o);
};
```

이렇게 하면 외부 함수 `Pr`가 `CMy` 클래스의 `private` 멤버 `a`에 접근할 수 있습니다.

---

### 🎯 학생들을 위한 학습 포인트

1. **캡슐화와 정보 은닉**: 클래스 내부의 private 멤버는 외부에서 직접 접근할 수 없다.
2. **friend 함수**: 예외적으로 특정 함수에게 접근 권한을 줄 수 있다.
3. **friend 선언 위치**: 클래스 내부에 선언하지만, 정의는 외부에서 해도 된다.

---

### 💡 참고

- friend 함수는 클래스의 멤버 함수가 **아님** → `CMy::Pr()`처럼 호출하지 않고 그냥 `Pr()`로 사용
- 객체가 함수의 인자로 전달되어도, friend가 아니면 그 객체의 `private` 멤버는 접근 불가

---

좋아요! 이 코드 예제를 바탕으로 학생들을 위한 **퀴즈 형식**과 **빈칸 채우기식 학습 자료**를 아래처럼 구성해보았습니다. C++ `friend` 키워드를 자연스럽게 익히게 만드는 데 목적이 있습니다.

---

## ✅ [학습 목표]
- 클래스의 `private` 멤버에 외부 함수가 접근할 수 있는지 이해한다.
- `friend` 키워드의 역할과 사용법을 익힌다.

---

## 🧠 Part 1. 퀴즈 (O/X 문제)

### Q1. 클래스 외부에서 정의된 함수는 클래스의 `private` 변수에 접근할 수 있다.  
➡️ (  )  

### Q2. `friend` 키워드를 이용하면 외부 함수도 클래스의 private 멤버에 접근할 수 있다.  
➡️ (  )  

### Q3. `friend` 함수는 클래스의 멤버 함수이다.  
➡️ (  )  

### Q4. 클래스 내부에서 friend 함수는 반드시 정의해야 한다.  
➡️ (  )

---

## ✏️ Part 2. 빈칸 채우기

다음 코드는 `CMy` 클래스의 `private` 변수 `a`를 외부 함수 `Pr`에서 출력하고자 합니다.  
빈칸에 알맞은 코드를 작성하세요.

```cpp
#include <iostream>
class CMy {
private:
    int a = 42;
public:
    // (1) 외부 함수 Pr에게 접근 권한을 주는 키워드 사용
    _______ void Pr(CMy o);
};

// (2) 외부 함수 정의
void Pr(CMy o) {
    std::cout << o.a << '\n';  // a는 private 멤버
}

int main() {
    CMy o;
    Pr(o);
    return 0;
}
```

> ✅ 정답:
> - (1) `friend`

---

## 💬 Part 3. 단답형

**Q1.** `friend` 함수는 클래스 내부에서 선언하고 외부에서 정의한다. 이때 클래스 내부에 작성하는 선언문 형태를 쓰시오.  
➡️ `___________________________________________`

> ✅ 예시 정답: `friend void Pr(CMy o);`

---

## ✅ [보너스 심화 문제]

**Q. 아래 코드에서 잘못된 부분을 찾고 수정하세요.**

```cpp
#include <iostream>
class CMy {
private:
    int a = 42;
public:
    void Pr(CMy o);  // (1)
};

void Pr(CMy o) {  // (2)
    std::cout << o.a << '\n';  // (3)
}
```

> 🔎 힌트: 외부 함수인데도 `private` 멤버 `a`에 접근하고 있음  
> 💡 정답:
> - (1) 줄에 `friend` 키워드를 추가해야 함: `friend void Pr(CMy o);`

---



