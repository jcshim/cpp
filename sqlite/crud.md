# **CRUD** 
### 데이터베이스를 다룰 때 자주 사용되는 **4가지 기본 작업**의 머리글자를 딴 용어

| 약어 | 의미     | SQL 문법   | 설명     |
| -- | ------ | -------- | ------ |
| C  | Create | `INSERT` | 데이터 삽입 |
| R  | Read   | `SELECT` | 데이터 조회 |
| U  | Update | `UPDATE` | 데이터 수정 |
| D  | Delete | `DELETE` | 데이터 삭제 |

---

### 🔹 예시로 보면 이해가 더 쉽습니다:

#### ✅ Create (데이터 삽입)

```sql
INSERT INTO students (name, age) VALUES ('Alice', 21);
```

#### ✅ Read (데이터 조회)

```sql
SELECT * FROM students WHERE age > 20;
```

#### ✅ Update (데이터 수정)

```sql
UPDATE students SET age = 22 WHERE name = 'Alice';
```

#### ✅ Delete (데이터 삭제)

```sql
DELETE FROM students WHERE name = 'Alice';
```

---

**요약:**

* `CRUD`는 데이터 **생성, 읽기, 수정, 삭제**의 핵심 기능을 의미합니다.
* SQLite뿐 아니라 MySQL, PostgreSQL, MongoDB, 심지어 파일 시스템에서도 기본이 되는 개념입니다.
