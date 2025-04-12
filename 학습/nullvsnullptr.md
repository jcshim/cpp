`nullptr`는 C++11에서 도입된 **null 포인터 상수**를 나타내는 키워드로, 기존의 `NULL` 또는 `0`을 사용하는 방식에서 발생할 수 있는 문제를 해결하기 위해 도입되었습니다.

---

## 🔹 `nullptr`의 주요 특징

- **타입 안전성**:`nullptr`는 `std::nullptr_t` 타입을 가지며, 이는 모든 포인터 타입으로 **암시적으로 변환**될 수 있지만, 정수 타입으로는 변환되지 않습니다
  
- **함수 오버로딩에서의 명확성**:`nullptr`를 사용하면 함수 오버로딩 시 어떤 함수가 호출될지 명확하게 결정됩니다

- **가독성 향상**:코드에서 포인터가 null인지 확인할 때 `if (ptr == nullptr)`와 같이 명확하게 표현할 수 있습니다

---

## 🔸 `nullptr` vs `NULL` vs `0`
기존에는 null 포인터를 나타내기 위해 `NULL` 매크로(보통 `0`으로 정의됨)나 직접 `0`을 사용했습니. 그러나 이 방식은 다음과 같은 문제를 일으킬 수 있습니다:

### 예제: 함수 오버로딩에서의 혼동

```cp
void func(int);
void func(char*);

func(NULL);  // 어떤 함수가 호출될까?
```

위 코드에서 `NULL`이 `0`으로 정의되어 있다면, `func(int)`가 호출됩니. 이는 개발자가 의도한 바와 다를 수 있습니.
하지만 `nullptr`를 사용하:

```cp
func(nullptr);  // func(char*)가 호출됩니.
```

이처럼 `nullptr`는 포인터 타입으로만 변환되므로, 함수 오버로딩 시 더 명확한 동작을 보장합니.

---

## 🔹 `std::nullptr_t` 타

`nullptr`의 타입은 `std::nullptr_t`이며, 이는 `<cstddef>` 헤더에 정의되어 있습다 이 타입은 모든 포인터 타입으로 암시적으로 변환될 수 있지만, 정수 타입으로는 변환되지 않습다.

### 예제: `std::nullptr_t`를 이용한 함수 오버로딩

```cp
#include <iostream>
#include <cstddef>

void func(int*) {
    std::cout << "Pointer to int\n";
}

void func(std::nullptr_t) {
    std::cout << "Null pointer\n";
}

int main() {
    func(nullptr);  // "Null pointer" 출력
    return 0
}
```


이 예제에서 `func(nullptr)`는 `std::nullptr_t` 타입의 매개변수를 받는 함수가 호출됩다.

---

## ✅ 결론
- `nullptr`는 C++11에서 도입된 null 포인터 상수로, 기존의 `NULL`이나 `0`을 사용하는 방식에서 발생할 수 있는 타입 관련 문제를 해결합다.- 함수 오버로딩 시 더 명확한 동작을 보장하며, 코드의 가독성과 안전성을 향상시킵다.- 따라서, C++11 이상을 사용하는 경우 null 포인터를 나타낼 때는 `nullptr`를 사용하는 것이 권장됩다.

더 자세한 내용은 [cppreference의 nullptr 문서](https://en.cppreference.com/w/cpp/language/nullptr)를 참고하실 수 있습다. 
