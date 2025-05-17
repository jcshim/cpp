# SQLite3과 MongoDB 모두를 C++에서 사용하는 
## **"학생 관리 시스템(Student Management System)"** 프로젝트

---

## ✅ 프로젝트 개요: **학생 관리 시스템**

* **기능**

  * 학생 등록 (이름, 학번, 전공 등)
  * 학생 목록 보기
  * 학생 정보 수정
  * 학생 삭제
  * SQLite3: 관계형 데이터베이스 연습용
  * MongoDB: 문서 지향(NoSQL) 데이터베이스 연습용

---

## 🔄 왜 이 프로젝트가 좋은가?

| 항목      | SQLite3            | MongoDB              |
| ------- | ------------------ | -------------------- |
| 데이터 구조  | 정형적 (테이블 스키마)      | 비정형적 (Document/JSON) |
| 학습 포인트  | SQL 문법, 테이블 설계     | BSON/Document 구조 이해  |
| CRUD 구현 | SQL 기반             | C++ 객체 → BSON 변환     |
| 파일 기반   | `.db` 파일로 로컬 저장    | 로컬 서버(또는 Atlas)에서 실행 |
| 쉬운 비교   | 정해진 스키마 vs 유연한 스키마 | 관계형 vs 문서형           |

---

## 🧱 프로젝트 구조 (C++ 기준)

```
/StudentManager/
├── main.cpp
├── sqlite_helper.cpp / .h   ← SQLite3 관련 함수들
├── mongo_helper.cpp / .h    ← MongoDB 관련 함수들
├── student.hpp              ← Student 구조체 정의
└── CMakeLists.txt (선택)
```

---

## 💾 예시: Student 구조체 (공통 사용)

```cpp
struct Student {
    int id;
    std::string name;
    std::string major;
};
```

---

## 🧪 SQLite3 예시 코드 (삽입)

```cpp
sqlite3* db;
sqlite3_open("students.db", &db);

std::string sql = "INSERT INTO students (id, name, major) VALUES (?, ?, ?);";
sqlite3_stmt* stmt;
sqlite3_prepare_v2(db, sql.c_str(), -1, &stmt, nullptr);

sqlite3_bind_int(stmt, 1, student.id);
sqlite3_bind_text(stmt, 2, student.name.c_str(), -1, SQLITE_STATIC);
sqlite3_bind_text(stmt, 3, student.major.c_str(), -1, SQLITE_STATIC);

sqlite3_step(stmt);
sqlite3_finalize(stmt);
sqlite3_close(db);
```

---

## 🧪 MongoDB 예시 코드 (삽입)

MongoDB C++ 드라이버(`mongocxx`) 설치 필요.

```cpp
mongocxx::client conn{mongocxx::uri{}};
auto db = conn["school"];
auto collection = db["students"];

bsoncxx::builder::stream::document document{};
document << "id" << student.id
         << "name" << student.name
         << "major" << student.major;

collection.insert_one(document.view());
```

---

## 📘 추천 학습 순서

1. **C++에서 SQLite3 연동** – CRUD 구현
2. **C++에서 MongoDB 연동** – CRUD 구현
3. **같은 UI / 구조로 두 버전 비교**
4. **정리: 두 DB의 차이점 및 장단점 요약**

---

## 🌟 확장 아이디어

* SQLite3에는 외래키로 **강의 테이블** 추가
* MongoDB에는 학생 문서 안에 **수강 과목 배열** 삽입
* 검색/필터 기능 구현 (이름으로 조회 등)
