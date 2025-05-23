아주 좋은 질문입니다! C++에서 람다식의 `[]` 괄호는 **캡처 리스트(capture list)**라고 불리며, 람다가 **외부 변수를 사용할 수 있도록 설정하는 곳**입니다. 비록 `[]`가 비어 있어도 **반드시 있어야 합니다.**

---

## 🔍 왜 `[]` 괄호가 **필수**일까?

### 이유 1️⃣: **문법적으로 람다임을 명시**
- C++에서 람다 함수는 `[]`로 시작하는 문법 구조입니다.
- 컴파일러는 `[]`가 있어야 "아, 이건 람다구나!" 하고 인식합니다.

예를 들어, 이건 람다 아님:
```cpp
() { return "Hi!"; }  // 컴파일 에러. 함수 정의처럼 보이지만 어딘가 붙일 대상 없음.
```

---

### 이유 2️⃣: 캡처 여부를 명확히 하기 위해

람다에서 외부 변수를 쓰고 싶을 때, `[]` 안에 명시적으로 써야 합니다:

```cpp
int a = 10;
auto f = [a]() { return a + 1; };  // 변수 a를 복사해서 캡처
```

`[]`가 없으면 이걸 표현할 방법이 없습니다.

---

### ✅ 정리하면:

| `[]` 형태 | 의미 |
|-----------|------|
| `[]`      | 아무 변수도 캡처하지 않음 (완전히 독립적인 람다) |
| `[a]`     | 변수 `a`를 **값으로 캡처** |
| `[&a]`    | 변수 `a`를 **참조로 캡처** |
| `[=]`     | **모든 외부 변수**를 값으로 캡처 |
| `[&]`     | **모든 외부 변수**를 참조로 캡처 |

---

### 🔧 예시 비교

```cpp
int x = 5;

// 캡처 안함 (x 사용 못함)
auto a = []() { /* x 사용 불가 */ };

// 값으로 캡처
auto b = [x]() { return x + 1; };

// 참조로 캡처
auto c = [&x]() { x += 1; return x; };
```

---

궁금하다면 "캡처가 실제 메모리상 어떤 영향을 주는지"나, "mutable 람다"까지 확장해서 설명해드릴게요!
