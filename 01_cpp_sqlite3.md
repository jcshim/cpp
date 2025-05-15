# **SQLite3**를 소개
---

## 🧠 SQLite3 소개 – C++에서 쓰기 전에 꼭 알아야 할 기초

---

### ✅ 1. SQLite3란?

> **SQLite3**는 **가장 가볍고 쉽게 사용할 수 있는 데이터베이스**입니다.
> 서버 없이 **하나의 파일**만으로 동작하는 "내장형(Relational Embedded) 데이터베이스 엔진"이에요.

---

### 🎯 2. SQLite3의 특징

* ✅ **가볍다** → 설치가 거의 필요 없음 (라이브러리만 있으면 됨)
* ✅ **파일 하나로 저장** → `.db` 또는 `.sqlite` 파일 하나로 모든 데이터 보관
* ✅ **SQL 지원** → `SELECT`, `INSERT`, `UPDATE` 등 표준 SQL 사용 가능
* ✅ **무료 & 오픈소스** → 누구나 사용 가능, 라이선스 걱정 없음
* ✅ **속도 빠름** → 소규모 프로젝트, 모바일 앱, 임베디드 장치 등에 적합

---

### 🔍 3. SQLite3는 어디에 쓰일까?

* 📱 스마트폰 앱 (예: 안드로이드 기본 DB)
* 📦 소형 IoT 기기
* 🧪 연구 데이터 관리
* 📝 간단한 데스크탑 앱의 설정 저장

---

### 💡 4. SQL 예제 (학생들이 쉽게 이해할 수 있게)

```sql
-- 학생 테이블 만들기
CREATE TABLE students (
    id INTEGER PRIMARY KEY,
    name TEXT,
    age INTEGER
);

-- 학생 추가
INSERT INTO students (name, age) VALUES ('홍길동', 21);

-- 모든 학생 조회
SELECT * FROM students;
```

이렇게 명령어(SQL)를 입력하면, SQLite가 데이터를 읽고, 저장하고, 출력합니다.

---

### ⚙️ 5. C++와 어떻게 연동할까?

SQLite는 `sqlite3.h` 헤더와 라이브러리를 통해 C/C++ 코드에서 사용할 수 있어요.
다음 시간에는 이 라이브러리를 통해 C++ 코드 안에서 데이터베이스를 직접 다루는 방법을 배울 거예요.

---

### 📌 요약

| 항목    | 설명                              |
| ----- | ------------------------------- |
| 종류    | 내장형 관계형 데이터베이스                  |
| 저장 방식 | 하나의 파일에 모든 데이터 저장               |
| 사용 언어 | SQL (Structured Query Language) |
| 장점    | 빠름, 가벼움, 무료, 설치 필요 없음           |
| 사용 예시 | 스마트폰 앱, 소형 장치, 간단한 데이터 저장       |

---
Raylib로 게임을 만들었을 때 `SQLite3 + C++`를 연동하면 **게임의 데이터를 저장하고 불러오는 기능**을 구현할 수 있습니다. 구체적으로는 다음과 같은 것들을 할 수 있습니다:

---

# 🎮 Raylib 게임 + SQLite3 연동 시 가능한 기능들

### ✅ 1. **세이브/로드 기능 구현**

* 플레이어 위치, 체력, 아이템, 레벨 등 게임 상태 저장
* 예시:

  ```cpp
  INSERT INTO saves (player_x, player_y, hp, level) VALUES (100, 250, 80, 3);
  ```

### ✅ 2. **하이스코어 저장**

* 최고 점수, 플레이어 이름 등을 기록하여 랭킹 시스템 구현
* 예시:

  ```cpp
  INSERT INTO highscores (name, score) VALUES ('Jae', 9870);
  SELECT name, score FROM highscores ORDER BY score DESC LIMIT 10;
  ```

### ✅ 3. **플레이어 프로필 시스템**

* 사용자 이름, 설정(볼륨, 해상도 등), 진행 정보 저장
* 로그인 시 불러오기 가능

### ✅ 4. **게임 내 상점 / 인벤토리 데이터 관리**

* 아이템 목록, 가격, 재고 등의 데이터를 DB에서 관리 가능
* 예: DB에서 상점 아이템 목록을 불러와 UI에 출력

### ✅ 5. **레벨/맵 정보 동적 로딩**

* 게임 맵, 적 위치, 오브젝트 등의 정보를 SQLite로 관리
* 맵을 자주 변경하는 게임에서 매우 유용 (툴로 편집 후 적용 가능)

### ✅ 6. **게임 이벤트 로깅**

* 게임 플레이 중 발생한 이벤트(예: 죽음 횟수, 아이템 획득 등)를 저장하여 분석
* 추후 통계 분석 or 리플레이 기능 구현 가능

### ✅ 7. **다국어 지원**

* 각 언어에 따른 문자열을 DB에 저장하고 필요 시 로딩
* 예: `SELECT text FROM strings WHERE key='start_button' AND lang='ko';`

---

## 🔧 예시 구조

```plaintext
게임 ←→ C++ 코드 ←→ SQLite3 데이터베이스
        ↑            ↑
      raylib       player.db
```

---

## 🧪 예: 하이스코어 저장 코드 (간단 예)

```cpp
sqlite3 *db;
sqlite3_open("game.db", &db);

std::string sql = "INSERT INTO highscores (name, score) VALUES ('Jae', 12345);";
sqlite3_exec(db, sql.c_str(), 0, 0, nullptr);

sqlite3_close(db);
```

---

## 🔄 실시간 데이터와 DB의 역할 분리

| 실시간 처리(Raylib) | 저장/관리(SQLite3) |
| -------------- | -------------- |
| 렌더링, 키 입력 등    | 세이브, 불러오기      |
| 물리 충돌, 애니메이션   | 하이스코어 저장       |
| UI 출력          | 설정 값 로딩        |

---
