### ✅ **C++11 (2011년)** — "Modern C++의 시작"
- `auto` 타입 추론
- 람다 함수 (`[](){}`)
- `nullptr`
- 범위 기반 for문 (`for (auto x : container)`)
- 스마트 포인터 (`std::unique_ptr`, `std::shared_ptr`)
- 이동 시맨틱스 (`std::move`, rvalue reference)
- `static_assert`
- `enum class`
- `constexpr`
- 템플릿 타입 추론 개선 (`typename`, `decltype`)
- `std::thread`, `std::mutex` 등 멀티스레딩 지원

---

### ✅ **C++14 (2014년)** — "C++11 개선판"
- 일반화된 람다 캡처 (`[=, x=std::move(x)]`)
- `auto` 반환 타입 추론
- `make_unique` 함수
- 바이너리 리터럴 (`0b1010`)
- `decltype(auto)`

---

### ✅ **C++17 (2017년)** — "더 간결하고 안전하게"
- 구조적 바인딩 (`auto [x, y] = pair;`)
- `if constexpr`
- `inline` 변수
- `std::optional`, `std::variant`, `std::any`
- `std::filesystem`
- `std::string_view`
- `constexpr if`
- `std::shared_mutex`

---

### ✅ **C++20 (2020년)** — "템플릿과 범위의 혁신"
- `concepts` (제너릭 타입 제약)
- `ranges` 라이브러리 (`views::filter`, `views::transform`)
- 코루틴 (`co_await`, `co_yield`, `co_return`)
- `modules` (모듈화)
- `consteval`, `constinit`
- `three-way comparison` (`<=>`, 우주선 연산자)
- 람다 캡처에서 템플릿 (`[x = T{}] <typename T>() {}`)

---

### ✅ **C++23 (2023년)** — "편의성과 라이브러리 확장"
- `std::expected` (예외 없는 에러 처리)
- `std::print`, `std::format` (Python 스타일 출력)
- `explicit` 생성자 기본값
- `constexpr`에서 `std::vector`, `std::string` 사용 가능
- `multidimensional subscript operator` (`a[i,j]`)
- 모듈화 개선 (`import std;`)

---

필요하시면 각 기능에 대한 예제도 제공해드릴 수 있어요!  
특정 버전이나 기능이 궁금하신가요?
