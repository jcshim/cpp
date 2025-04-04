
# **RAII (Resource Acquisition Is Initialization)**

1. **자원을 안전하고 효율적으로 관리하는 핵심 철학** 
2. 특히 Vulkan처럼 리소스를 많이 다루는 API에서는 **RAII를 잘 활용하는 것이 안정성과 성능 모두에 큰 도움**

---

## 💡 RAII란?

**RAII = 자원의 획득이 곧 초기화다**  
즉, 어떤 리소스를 "얻는 순간" 객체가 초기화되고, **스코프를 벗어나면 자동으로 정리(destructor 호출)**되는 구조예요.

---

### 📦 쉽게 말하면?

- **객체가 생성될 때** 자원(메모리, 파일, 소켓, 락 등)을 확보하고  
- **객체가 소멸될 때** 자원을 자동으로 반납

---

## 🎯 왜 RAII가 중요할까?

| 장점 | 설명 |
|------|------|
| ✅ 예외 안전 | 예외가 발생해도 자원이 자동으로 정리됨 |
| ✅ 메모리 누수 방지 | new/delete, malloc/free 실수 줄임 |
| ✅ 코드 간결화 | try-catch-finally 없이도 정리 가능 |
| ✅ 관리 용이성 | 리소스가 객체 수명과 자동 연동됨 |

---

## 📌 예제: 파일 열기/닫기 (RAII 미사용 vs 사용)

### ❌ RAII를 사용하지 않은 예
```cpp
void readFile() {
    FILE* file = fopen("data.txt", "r");
    if (!file) return;

    // 예외 발생 시 fclose()가 호출 안될 수 있음
    // ...
    fclose(file);
}
```

### ✅ RAII를 적용한 예 (`std::ifstream`)
```cpp
void readFile() {
    std::ifstream file("data.txt");
    if (!file) return;

    // file 객체가 함수 끝나면 자동으로 닫힘!
    std::string line;
    while (std::getline(file, line)) {
        std::cout << line << std::endl;
    }
}
```

---

## 🧱 사용자 정의 RAII 예제

```cpp
class FileRAII {
public:
    FileRAII(const char* filename) {
        file = fopen(filename, "r");
    }

    ~FileRAII() {
        if (file) fclose(file);
    }

    FILE* get() const { return file; }

private:
    FILE* file;
};

// 사용
void read() {
    FileRAII f("log.txt");
    if (!f.get()) return;

    // 여기서 f는 자동으로 fclose됨
}
```

---

## 🔄 Vulkan에서의 RAII 활용 예

Vulkan에서는 이런 패턴이 특히 많이 등장해요:

```cpp
class VkInstanceRAII {
public:
    VkInstanceRAII() {
        // vkCreateInstance(...)
    }

    ~VkInstanceRAII() {
        // vkDestroyInstance(...)
    }

    VkInstance get() const { return instance; }

private:
    VkInstance instance;
};
```

Vulkan에선 수십 개의 `create/destroy` 쌍을 관리해야 하므로,  
**RAII 클래스 또는 smart pointer 래퍼를 쓰면 훨씬 안전하고 깔끔**해요.

---

## 📚 핵심 요약

- RAII는 C++에서 자원을 안전하게 관리하는 **모범 사례**
- 생성자 = 자원 할당, 소멸자 = 자원 정리
- 파일, 메모리, 락, 소켓, Vulkan 객체 등 **모든 자원에 적용 가능**
- Vulkan이나 OpenGL처럼 리소스 중심 API에서 매우 중요!

---

필요하시면 `unique_ptr`, `shared_ptr`, `std::lock_guard` 등 STL 기반 RAII 도구나,  
**Vulkan 프로젝트에서 사용하는 실제 RAII 클래스 구조 예시**도 보여드릴게요!  
더 깊이 들어가볼까요? 😊
