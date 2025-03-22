### 코드 설명

```cpp
#include <iostream>  // 표준 입출력 사용을 위한 헤더
#include <vector>    // vector 컨테이너 사용을 위한 헤더

int main() {
    std::vector<int> v = {1, 2, 3};  // 정수 벡터 v에 1, 2, 3 저장
    int sum = 0;                     // 합을 저장할 변수 초기화
    for (int x : v) sum += x;        // 범위 기반 for문으로 벡터의 모든 값을 sum에 더함
    std::cout << sum << std::endl;   // 결과 출력 (6)
}
```

---

### 요약

- `vector<int>`에 1, 2, 3 저장  
- `for` 문으로 모든 값을 더해 `sum` 계산  
- 결과(6)를 출력
