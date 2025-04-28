### 1. **STL (Standard Template Library)**  
→ 자료구조와 알고리즘을 일반화된 템플릿 형태로 제공하는 C++ 라이브러리.

---

## [ 컨테이너 (Containers) ]
- **vector** : 동적 배열(Dynamic Array)을 구현한 연속 저장 컨테이너.
- **list** : 양방향 연결 리스트(Double Linked List) 컨테이너.
- **deque** : 양쪽 끝에서 삽입과 삭제가 가능한 이중 덱(Double Ended Queue).
- **array** : 고정 크기의 정적 배열(Static Array) 래퍼 컨테이너.
- **forward_list** : 단방향 연결 리스트(Singly Linked List) 컨테이너.
- **stack** : 후입선출(LIFO) 구조를 제공하는 어댑터 컨테이너.
- **queue** : 선입선출(FIFO) 구조를 제공하는 어댑터 컨테이너.
- **priority_queue** : 우선순위 큐(Priority Queue)를 제공하는 어댑터 컨테이너.
- **set** : 중복을 허용하지 않고 자동 정렬되는 키 컨테이너.
- **multiset** : 중복을 허용하며 자동 정렬되는 키 컨테이너.
- **map** : 키-값 쌍(pair)을 저장하고 키를 기준으로 자동 정렬하는 컨테이너.
- **multimap** : 키 중복을 허용하는 map 컨테이너.
- **unordered_set** : 해시 기반 비정렬 set 컨테이너.
- **unordered_multiset** : 해시 기반 비정렬 multiset 컨테이너.
- **unordered_map** : 해시 기반 비정렬 map 컨테이너.
- **unordered_multimap** : 해시 기반 비정렬 multimap 컨테이너.

---

## [ 이터레이터 (Iterators) ]
- **iterator** : 컨테이너 원소를 순회(iteration)하는 객체.
- **const_iterator** : 읽기 전용 순회용 이터레이터.
- **reverse_iterator** : 뒤에서 앞으로 순회하는 이터레이터.
- **back_inserter** : 컨테이너 끝에 삽입하는 이터레이터 어댑터.
- **front_inserter** : 컨테이너 앞에 삽입하는 이터레이터 어댑터.
- **inserter** : 지정 위치에 삽입하는 이터레이터 어댑터.
- **istream_iterator** : 입력 스트림을 순회하는 이터레이터.
- **ostream_iterator** : 출력 스트림에 데이터를 쓰는 이터레이터.

---

## [ 알고리즘 (Algorithms) ]
- **sort** : 범위를 정렬하는 알고리즘.
- **find** : 특정 값을 검색하는 알고리즘.
- **binary_search** : 이진 탐색 알고리즘 (정렬된 범위에서 사용).
- **lower_bound** : 특정 값 이상이 처음 나타나는 위치를 찾는 알고리즘.
- **upper_bound** : 특정 값을 초과하는 첫 번째 위치를 찾는 알고리즘.
- **equal_range** : 특정 값의 구간을 찾는 알고리즘.
- **copy** : 한 범위의 원소를 다른 범위로 복사하는 알고리즘.
- **fill** : 범위를 주어진 값으로 채우는 알고리즘.
- **remove** : 특정 값을 제거(실제 삭제는 아님)하는 알고리즘.
- **unique** : 연속된 중복 원소를 제거하는 알고리즘.
- **accumulate** : 범위의 값을 합산(누적)하는 알고리즘.
- **for_each** : 범위 내의 각 원소에 대해 함수 호출을 수행하는 알고리즘.
- **partition** : 조건에 따라 범위를 분할하는 알고리즘.
- **merge** : 두 개의 정렬된 범위를 하나로 합치는 알고리즘.

---

## [ 함수 객체 (Function Objects, Functors) ]
- **function** : 가변 호출 객체를 다루는 클래스(함수, 람다, 객체 호출 가능).
- **bind** : 함수 호출 인자를 고정하거나 재배치하는 어댑터.
- **mem_fn** : 멤버 함수를 일반 함수처럼 호출할 수 있게 변환하는 도구.
- **greater**, **less**, **equal_to** 등 : 비교 연산자 함수 객체.

---

## [ 어댑터 (Adapters) ]
- **stack** : 내부 컨테이너를 쌓아 사용하는 어댑터.
- **queue** : 내부 컨테이너를 선입선출로 사용하는 어댑터.
- **priority_queue** : 내부 컨테이너를 우선순위 큐로 사용하는 어댑터.

---

## [ 유틸리티 (Utilities) ]
- **pair** : 두 값을 하나로 묶는 구조체 템플릿.
- **tuple** : 여러 값을 하나로 묶는 구조체 템플릿.
- **make_pair** : pair를 생성하는 헬퍼 함수.
- **make_tuple** : tuple을 생성하는 헬퍼 함수.
- **move** : 객체를 이동(moving)하는 함수 (rvalue 참조 활용).
- **forward** : 완벽 전달(perfect forwarding)을 지원하는 함수.
- **swap** : 두 값을 효율적으로 교환하는 함수.
- **declval** : 타입만 필요한 상황에서 임시 객체를 만들어주는 헬퍼.

---

## [ 메모리 관리 (Memory Management) ]
- **allocator** : 메모리 할당 방식을 정의하는 클래스(컨테이너 기본 할당자).
- **get_allocator** : 컨테이너에 사용 중인 allocator를 가져오는 함수.

---

## [ 기타 STL 핵심 요소 ]
- **bitset** : 고정 크기 비트 배열(Bit Array) 관리 클래스.
- **regex** : 정규 표현식을 다루는 라이브러리.
- **chrono** : 시간과 기간(Duration)을 다루는 시간 라이브러리.
- **random** : 난수 생성 및 분포 라이브러리.
- **thread** : 다중 스레드 프로그래밍을 지원하는 라이브러리.
- **mutex** : 스레드 동기화용 뮤텍스 클래스.

---

✅ **요약**  
STL은 **컨테이너(Container)**, **이터레이터(Iterator)**, **알고리즘(Algorithm)**, **함수 객체(Function Object)**, **어댑터(Adapter)**, **유틸리티(Utility)** 등을 포괄하며, 현대 C++ 프로그래밍의 핵심을 이루는 표준 템플릿 집합입니다.

---

**필요하면** 위 목록을 "카테고리별 표로 보기"나 "학습용 요약 노트 스타일"로도 다시 정리해드릴 수 있습니다.  
추가로 "STL 키워드별 예제 코드"도 요청하실까요? 🚀
(예: vector 사용 예제, sort 사용 예제 등)
