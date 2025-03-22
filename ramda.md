C++에서 **람다(lambda) 함수**를 사용하여 두 수를 더하는 가장 간단한 형태

```cpp
auto add = [](int a, int b) { return a + b; };
```

이렇게 작성하면 `add`는 두 개의 `int`를 받아서 더한 값을 반환하는 함수 객체가 됩니다. 사용 예시는 다음과 같습니다:

```cpp
#include <iostream>

int main() {
    auto add = [](int a, int b) { return a + b; };
    std::cout << add(3, 5) << std::endl;  // 출력: 8
    return 0;
}
```

조금 더 간단하게, **즉석에서 호출**할 수도 있습니다:

```cpp
#include <iostream>

int main() {
    std::cout << [](int a, int b) { return a + b; }(3, 5) << std::endl;  // 출력: 8
    return 0;
}
```

이건 람다를 변수에 저장하지 않고 곧바로 호출하는 방식입니다.  
필요한 스타일에 따라 골라서 쓰면 돼요!
