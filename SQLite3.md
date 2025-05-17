# SQLite3 

목표:

* SQLite3의 기본 개념 이해
* 간단한 데이터베이스 생성 및 조작 실습
* SQL 기본 문법 익히기 (SELECT, INSERT, UPDATE, DELETE 등)
* C/C++ 연동 예제까지 가볍게 시도해보기

---

## ✅ 1시간차: SQLite와 SQL 기초 개념 익히기

**목표**: 데이터베이스와 SQLite3의 기본 개념을 이해하고, SQLite CLI 환경 익히기

### 🔹 학습 주제

* RDBMS란? (DB, Table, Row, Column)
* SQLite3의 특징 (파일 기반, 설치 없이 사용 가능 등)
* SQLite3 설치 및 CLI 실행

  * 설치: [https://www.sqlite.org/download.html](https://www.sqlite.org/download.html)
  * CLI 실행: `sqlite3 mydb.db`
* 기본 명령어

  * `.help`, `.tables`, `.schema`, `.exit`

### 🔹 실습

```sql
-- DB 접속 후
CREATE TABLE students (
  id INTEGER PRIMARY KEY,
  name TEXT,
  age INTEGER
);

INSERT INTO students (name, age) VALUES ('Alice', 21);
INSERT INTO students (name, age) VALUES ('Bob', 22);

SELECT * FROM students;
```

---

## ✅ 2시간차: SQL 기본 문법 연습 (CRUD 중심)

**목표**: SQL을 이용한 데이터 삽입/조회/수정/삭제 실습

### 🔹 학습 주제

* SQL 기본 구조

  * `SELECT`, `WHERE`, `INSERT`, `UPDATE`, `DELETE`
* 조건 검색, 정렬, LIMIT, LIKE

### 🔹 실습 예제

```sql
-- 조건 검색
SELECT * FROM students WHERE age > 21;

-- 데이터 수정
UPDATE students SET age = 23 WHERE name = 'Bob';

-- 데이터 삭제
DELETE FROM students WHERE id = 1;

-- LIKE 검색
SELECT * FROM students WHERE name LIKE 'A%';
```

---

## ✅ 3시간차: C/C++에서 SQLite3 사용해보기

**목표**: C++에서 SQLite3을 어떻게 사용하는지 간단한 예제 통해 이해

### 🔹 준비

* Visual Studio 또는 g++ 컴파일러
* SQLite3 헤더/라이브러리 (Windows에서는 NuGet 패키지: `sqlite3`)

### 🔹 기본 C 코드 예제

```cpp
#include <stdio.h>
#include <sqlite3.h>

int main() {
    sqlite3 *db;
    char *errMsg = 0;

    // DB 열기
    if (sqlite3_open("mydb.db", &db)) {
        printf("Can't open DB: %s\n", sqlite3_errmsg(db));
        return 1;
    }

    // SQL 실행
    const char *sql = "CREATE TABLE IF NOT EXISTS test (id INTEGER PRIMARY KEY, name TEXT);";
    if (sqlite3_exec(db, sql, 0, 0, &errMsg) != SQLITE_OK) {
        printf("SQL error: %s\n", errMsg);
        sqlite3_free(errMsg);
    }

    sqlite3_close(db);
    return 0;
}
```

---

## 🔚 정리 및 추천 자료

* [공식 SQLite 튜토리얼](https://www.sqlitetutorial.net/)
* YouTube 검색: “SQLite3 입문 강의”
* SQL 연습 사이트: [https://sqlfiddle.com](https://sqlfiddle.com), [https://www.w3schools.com/sql/](https://www.w3schools.com/sql/)

---
