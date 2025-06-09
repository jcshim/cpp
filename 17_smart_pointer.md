# smart_pointer

## ✅ 스마트 포인터 종류

| 스마트 포인터              | 설명                                     |
| -------------------- | -------------------------------------- |
| `std::unique_ptr<T>` | 소유권이 하나인 객체                            |
| `std::shared_ptr<T>` | 참조 카운트 기반 공유 소유 객체                     |
| `std::weak_ptr<T>`   | `shared_ptr`를 참조하되 소유권은 없음 (순환 참조 방지용) |

---

## ✅ 스마트 포인터 생성 함수

| 함수                         | 설명                                           |
| -------------------------- | -------------------------------------------- |
| `std::make_unique<T>(...)` | C++14부터 도입. 예외 안전하고 간결한 `unique_ptr` 생성 방식   |
| `std::make_shared<T>(...)` | `shared_ptr`을 효율적으로 생성 (참조 카운트와 객체를 한 번에 할당) |

---

## ✅ 유용한 멤버 함수 및 관련 함수

### 📌 공통 (unique\_ptr / shared\_ptr)

| 함수/기능          | 설명                                       |
| -------------- | ---------------------------------------- |
| `.get()`       | 생 포인터(raw pointer)를 가져옵니다 (주의해서 사용)      |
| `.reset()`     | 현재 객체와의 연결을 끊고 스마트 포인터를 초기화              |
| `.release()`   | `unique_ptr` 전용. 생 포인터 반환 후 소유권 해제       |
| `.use_count()` | `shared_ptr` 전용. 참조 횟수 반환                |
| `.unique()`    | `shared_ptr` 전용. 자신만 객체를 소유하고 있는지 확인     |
| `.expired()`   | `weak_ptr` 전용. 참조 대상이 소멸되었는지 확인          |
| `.lock()`      | `weak_ptr` → `shared_ptr`로 승격 (유효한 경우에만) |

---

## ✅ 기타 유용한 기능

### 📌 커스텀 삭제자(Custom deleter)

```cpp
std::unique_ptr<MyClass, void(*)(MyClass*)> ptr(new MyClass, [](MyClass* p) {
    std::cout << "삭제자 호출\n";
    delete p;
});
```

* 리소스 해제를 사용자 정의할 수 있습니다 (예: 파일 닫기, 메모리 맵 해제 등)

---

### 📌 배열 지원 (unique\_ptr만)

```cpp
std::unique_ptr<int[]> arr(new int[10]); // 스마트 배열
arr[0] = 42;
```

---

### 📌 스마트 포인터 + 컨테이너 조합

```cpp
std::vector<std::shared_ptr<MyClass>> objects;
objects.push_back(std::make_shared<MyClass>());
```

* `std::shared_ptr`는 `std::vector`, `std::map` 등과 잘 어울립니다.

---

## 🔥 요약표

| 기능             | unique\_ptr | shared\_ptr | weak\_ptr |
| -------------- | ----------- | ----------- | --------- |
| `.get()`       | ✅           | ✅           | ❌         |
| `.reset()`     | ✅           | ✅           | ❌         |
| `.release()`   | ✅           | ❌           | ❌         |
| `.use_count()` | ❌           | ✅           | ✅         |
| `.lock()`      | ❌           | ❌           | ✅         |
| `.expired()`   | ❌           | ❌           | ✅         |

---

## 📌 참고

* `std::enable_shared_from_this<T>`
  → 클래스 내부에서 자신에 대한 `shared_ptr`을 안전하게 얻을 수 있게 해주는 기능입니다.

```cpp
class MyClass : public std::enable_shared_from_this<MyClass> {
public:
    std::shared_ptr<MyClass> getPtr() {
        return shared_from_this();
    }
};
```
