# mongodb
## 설치

# mongosh

## ✅ Step 1: 데이터베이스 선택 또는 생성

MongoDB는 `use` 명령어로 데이터베이스를 선택하며, 존재하지 않으면 자동으로 생성됩니다.

```javascript
use testdb
```

→ `switched to db testdb` 라고 나오면 성공입니다.

---

## ✅ Step 2: 컬렉션 생성 + 문서 삽입

MongoDB에서는 컬렉션도 명시적으로 만들 필요 없이, 문서를 삽입하면 자동 생성됩니다.

```javascript
db.students.insertOne({ name: "Alice", age: 21 })
```

→ 성공 시: `{ acknowledged: true, insertedId: ObjectId(...) }`

---

## ✅ Step 3: 데이터 조회 (Read)

```javascript
db.students.find()
```

→ 삽입한 문서가 출력됩니다.

또는 예쁘게 보기:

```javascript
db.students.find().pretty()
```

---

## ✅ Step 4: 여러 문서 삽입

```javascript
db.students.insertMany([
  { name: "Bob", age: 20 },
  { name: "Charlie", age: 23 },
  { name: "Diana", age: 22 }
])
```

---

## ✅ Step 5: 조건 검색

```javascript
db.students.find({ age: { $gt: 21 } })  // 21세 초과
```

---

## ✅ Step 6: 문서 수정

```javascript
db.students.updateOne(
  { name: "Alice" },
  { $set: { age: 25 } }
)
```

---

## ✅ Step 7: 문서 삭제

```javascript
db.students.deleteOne({ name: "Bob" })
```

---

## ✅ Step 8: 컬렉션 목록 확인

```javascript
show collections
```

---

## 📌 한눈에 보는 초보자용 실습 명령어 모음

| 작업        | 명령어                                                 |
| --------- | --------------------------------------------------- |
| 데이터베이스 선택 | `use testdb`                                        |
| 문서 삽입     | `db.students.insertOne({ name: "Alice", age: 21 })` |
| 여러 문서 삽입  | `insertMany([...])`                                 |
| 문서 조회     | `db.students.find()`                                |
| 조건 조회     | `{ age: { $gt: 21 } }`                              |
| 문서 수정     | `updateOne({조건}, { $set: {변경} })`                   |
| 문서 삭제     | `deleteOne({조건})`                                   |

---

## 🔁 추천 실습 미션

아래 미션을 직접 해보세요:

1. 데이터베이스 `library` 생성
2. 컬렉션 `books` 생성
3. 책 3권 입력 (`title`, `author`, `year`)
4. 2015년 이후 책만 조회
5. 특정 책의 제목을 수정
6. 책 한 권 삭제

---
