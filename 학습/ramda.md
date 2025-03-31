
# 람다 함수(lambda function): 
## 짧고 간결한 함수를 필요한 순간에 바로 정의해서 씀

### ✅ 왜 람다 함수를 사용할까?

1. **짧게 쓰고 바로 사용하고 싶을 때**  
   - 함수 이름 만들고 따로 선언할 필요 없이 한 줄로 끝!
   ```cpp
   auto square = [](int x) { return x * x; };
   ```

2. **함수 전달이 필요할 때** (예: `std::sort`, `std::for_each`)  
   - 람다로 정렬 기준을 바로 작성!
   ```cpp
   sort(v.begin(), v.end(), [](int a, int b) { return a > b; });
   ```

3. **바깥 변수(상태)를 캡처해서 함께 쓸 수 있음**  
   - 외부 변수도 함수 안에서 자연스럽게 사용
   ```cpp
   int offset = 10;
   auto add = [offset](int x) { return x + offset; };
   ```

4. **간단한 콜백 함수 정의에 딱 좋음**  
   - GUI 이벤트, 스레드, 반복자 콜백 등에 자주 씀
   ```cpp
   thread t([](){ cout << "스레드 실행!\n"; });
   ```

---

### 📌 정리 한 줄 요약

> **람다 함수는 "간단한 동작을 빠르게 정의하고 바로 쓰고 싶을 때" 딱 좋은 도구!**

---

### ✅ 예제 코드

```cpp
#include <iostream>
using namespace std;

int main() {
    auto add = [](int a, int b) { return a + b; };
    cout << add(3, 5);  // 출력: 8
}
```

---

### 🔍 설명

- `auto add = [](int a, int b) { return a + b; };`  
  → 두 정수를 더해서 반환하는 람다 함수 생성
- `add(3, 5)` → 3 + 5 = 8 출력

