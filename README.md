# 🔥 Tech-Interview

## 🏷 INDEX

- [JAVA](#JAVA)
- [SPRING](#SPRING)
- [DATABASE](#DATABASE)
- [KOTLIN](#KOTLIN)


<br>
<br>


## JAVA

<details>
<summary>Stream이란?</summary>

<br>

- 선언형 방식으로 컬렉션의 데이터를 조작하는 API
- 외부 반복을 통해 작업하는 컬렉션과 달리 내부 반복을 통해 작업 수행
- 스트림은 재사용이 가능한 컬렉션과 달리 한번만 사용 (=불변)
- 지연 연산을 통해 성능 최적화

---

</div>
</details>

<br>


<details>
<summary>객체지향/함수형 프로그래밍</summary>

<br>

- 함수형 프로그래밍
  - 함수의 인자를 통해 불변값을 돌려주는 프로그래밍
- 객체지향형 프로그래밍
  - 상태와 행위를 가진 객체를 만들고 객체간 상호작용을 통해 로직을 구성하는 프로그래밍

---

</div>
</details>

<br>


<details>
<summary>Lamdba식이란? (+ 익명 클래스) </summary>

<br>

- 함수를 변수처럼 사용하는 것.
- 익명 클래스 메서드를 단순화하여 클래스를 생성하지 않는다.
  - 익명 클래스 : 클래스 정의와 동시에 객체를 생성하는 클래스
    ```java
    Pomo pomo = new Pomo() {
        public int age = 100;

        @Override
        public int getAge() {
            return this.age;
        }
    }
    ```
- 매개변수에 대한 타입은 런타임시 자동으로 인식되어 생략 가능

---

</div>
</details>

<br>

<details>
<summary>Java8에 추가된 기능</summary>

<br>

- 함수형 프로그래밍을 지원 (stream, lambda)
- LocalDate, LocalDateTime 클래스 
- 인터페이스의 default 메서드
- Optional

---

</div>
</details>

<br>

<details>
<summary>Map vs FlatMap</summary>

<br>

- map : 단일 스트림 안의 요소를 원한느 특정 형태로 변환 시켜주는 중간 연산 메서드
- flatmap : 요소가 리스트일 때 각 리스트의 모든 원소를 특정 형태로 변환하고 단일 원소 스트림으로 반환시켜주는 중간 메서드

---

</div>
</details>

<br>

<details>
<summary>String/StringBuilder/StringBuffer</summary>

<br>

| String | StringBuffer | StringBuilder |
|---|---|---|
|불변|가변|가변|
| - | 많은 문자열 연산 시 효율적 | 많은 문자열 연산시 효율적|
| - | equals 메서드 오버라이딩 X | StringBuffer - 스레드 동기화 기능 |

- 스레드 동기화를 뺀 StringBuilder의 성능이 더 빠르다.

---

</div>
</details>

<br>

<details>
<summary>HashMap/HashTable/ConcurrentHashMap</summary>

<br>

- Map 인터페이스로 구현한 구현체로 key:value 구조를 가진다.

<br>

**Thread-Safe**

| HashMap | HashTable | ConcurrentHashMap |
|---|---|---|
| `synchronized` 키워드가 없어 thread-safe X | `synchronized` 키워드가 있어 thread-safe O | `synchronized` 키워드가 없지만 thread-safe O |
| null 허용 | null 허용 X | null 허용 X |


- 찾고자 하는 버킷 접근 시 모든 버킷을 잠그는 HashTable과 달리 ConcurrentHashMap은 해당 해시 버킷만을 잠금

<br>

### 조회
- HashMap : Hashing을 사용해 데이터를 저장하기 때문에 조회시 O(1)
- TreeMap : Red-black 트리를 사용해 데이터를 저장하기 때문에 조회 시 O(logN)

### 데이터 순서
- HashMap : 순서 보장 X
- TreeMap & LinkedHashMap : 순서 보장 O

---

</div>
</details>

<br>

<details>
<summary>JVM 메모리 구조</summary>

<br>

- JVM 내에 있는 클래스 로더가 런타임 데이터 영역로 바이트 코드 파일 적재

**Runtime Data Aread**

| method(static 영역) | Heap | Stack | PC(Program counter ) | native method stack |
|:--:|:--:|:--:|:--:|:--:|
| 클래스 수준 정보, static 데이터 | GC 대상이 되는 new를 통해 생성되는 객체와 배열 저장 | 메서드 스택 프레임 생성 영역 | native가 붙어있고, c/c++로 돌아가는 콜 스택 |
| 스레드 공유 자원 O | 스레드 공유 자원 O | 스레드 공유 자원 X | - | JNI를 호출해 메서드 실행 |

- JIT 컴파일러 : 바이트 코드 전체 -> 컴파일 -> 바이너리 코드, 인터프리팅 하지 않고 바이너리 코드 실행

---

</div>
</details>

<br>

<details>
<summary>자바 프로그래밍 동작 과정</summary>

<br>

1. .java -> (컴파일러 `javac`) -> .class(바이트코드) 변환 (JVM을 위한 기계어로 변환)
2. JVM 내에 있는 클래스 로더가 런타임 데이터 영역으로 바이트 코드 파일 적재
  - Loading(클래스 읽기) -> Linking(레퍼런스 연결) -> initializing(정적 변수 초기화, 할당)
3. JVM 내에 있는 실행 엔진(interpreter, JIT compiler, GC)이 런타임 데이터 영역에 적재된 바이트 코드를 기계어로 변경해 명령어 단위로 실행.
  - 인터프리팅은 기계어로 변환하는 즉, 플랫폼에 종속되지 X

---

</div>
</details>

<br>

<details>
<summary>로깅을 사용 이유</summary>

<br>

- 일반 출력은 멀티 스레드 환경에서 synchronized 키워드를 통해 thread-safe를 보장하여 성능 하락
- 로그는 시스템 콘솔에만 출력 되고 일반 출력은 로그 레벨을 설정 불가능
- 로깅 라이브러리를 통한 많은 부가 정보(스레드 정보, 클래스 이름) 제공
- 시스템 콘솔 이외에도 파일이나 특정 서버로 보내는 등의 저장이 가능
- 로그는 비동기적인 동작이 가능 

---

</div>
</details>

<br>

<details>
<summary>Checked Exception vs Unchecked Exception</summary>

<br>

| checked | unchecked | 
|---|---|
| 별도의 예외 처리를 하지 않으면 컴파일 단계에서 오류 발생 (비관적 예외 처리 기법) | 별도의 예외 처리를 하지 않아도 컴파일 단계에서 오류 발생 X (낙관적 예외 처리 기법) |
| SQL Exception, IOException | NPE, RuntimeException |


**checkd exception을 지양하는 이유?**
- OCP 위반 : 모든 상위 메서드들이 최하위 메서드의 예외 시그니처를 알아야하므로 캡슐화 X
- depth가 깊어지면 예외 발생 근원도 알기 어렵다.

---

</div>
</details>

<br>

<details>
<summary>자바 직렬화</summary>

<br>

- 직렬화 : 데이터를 연속적인 데이터(바이트 스트림)로 변형
  - 객체 👉 스트림 (전송 혹은 저장하기 위함)
- 역직렬화 : 직렬화된 데이터를 변환하여 객체의 형태로 표현
  - 스트림 👉 객체  (전송 혹은 저장된 것을 다시 객체로 사용하기 위함)


**SUID(SerialVersionUID)**
- `java.io.Serializable` 인터페이스를 통해 직렬화/역직렬화 가능
- 직렬화 대상 객체는 동일한 SUID를 갖는다.
- 직접 설정해주지 않아도 **자동으로 해시값이 할당**
  - 직렬화 <-> 역직렬화 과정에서 클래스 정보의 변경이 일어날 경우 `ClassCastException` 발생
- 직접 지정하여 관리함(필드로 가짐)으로써 예외 발생을 막을 수 있지만 데이터 누락이 있을 수 있다.


---

</div>
</details>

<br>

<details>
<summary>동기화/비동기화</summary>

<br>

- 동기화 : 프로세스/스레드들이 동시에 실행되며 서로 끼어들지 않음. (Lock 처리)
- 비동기화 : 어느 메서드를 실행하는 도중 다시 메서드 실행이 가능 (멀티 스레드)

---

</div>
</details>

<br>

<details>
<summary>Thread-Safe</summary>

<br>

- 여러 스레드로부터 동시 접근이 이루어져도 프로그램 실행에 문제가 없다.
- `synchronized` 키워드, `ConcurrentHashMap` 등
- Lock이나 세마포어를 걸어 1공유자원 1접근 혹은 Thread-Local로 동시 접근을 막거나 불변 객체로 값을 변경할 수 없도록 막는다.

---

</div>
</details>

<br>

<details>
<summary>해시 충돌</summary>

<br>

- java7까지는 LinkedList를 이용한 sepereate chaining
- java8부터 linked list와 red black tree 혼용 (임계치를 넘어가면 변경)

---

</div>
</details>

<br>

<details>
<summary>Atomic, volatile, synchronized</summary>

<br>

**Atomic**
- 멀티 스레드 환경에서 CPU는 메인 메모리에서 변수값을 참조하는 것이 아닌 캐시 영역의 값을 참조한다.
- 이때 메인 메모리 값 != 캐시 값 발생 가능성 👉 CAS 알고리즘 사용
  - 스레드 값(캐시값)과 메인 메모리 값을 비교하여 일치하면 새로운 값을 교체 
  - 일치하지 않으면 재시도

**synchronized**
- lock을 걸어 동기화

**volatile**
- CPU 캐시가 아닌 메모리에서 값을 참조 👉 **변수값 불일치 문제 해결**
- 멀티 스레드 환경에서 1개만 읽기/쓰기, 나머지는 읽기만 하는 상황에서 가장 최신값을 보장

---

</div>
</details>

<br>

<details>
<summary>정적/동적 바인딩</summary>

<br>

- 바인딩 : 프로그램 구성 요소의 성격을 결정
- 정적 바인딩 : 컴파일 타임에 성격이 결정
  - C, C++, JAVA
- 동적 바인딩 : 다형성을 사용해 메서드를 호출할 때 발생하는 현상. 런타임에 성격이 결정
  - python, kotlin

---

</div>
</details>

<br>

<details>
<summary>자바 프로그램 동작 과정</summary>

<br>

1. java -> (컴파일러 javac) -> 바이트코드(.class) 변환 (JVM을 위한 기계어 변환)
2. JVM 내에 있는 클래스 로더가 런타임 데이터 영역으로 바이트 코드 파일 적재
  - Loading (클래스 읽기) -> Linking(레퍼런스 연결) -> Initializaing (정적 변수 초기화, 할당)
3. JVM 내에 있는 실행 엔진(Interpreter, JIT Compiler, GC)이 런타임 데이터 영역에 적재된 바이트 코드를 기계어로 변경해 명령어 단위로 실행
  - 인터프리팅은 기계어로 변환하는 즉, 플랫폼 종속 X

---

</div>
</details>

<br>

<details>
<summary>Reflection</summary>

<br>

- 클래스 로더에 의해 Method 영역에 로딩되어있는 클래스 메타데이터를 이용해 해당 클래스의 인스턴스를 생성하거나 멤버에 접근할 수 있도록 도와주는 자바 API
- ex. ComponentScan, DinamicProxy

**주의할 점**
- 성능 이슈 : ComponentScan처럼 한번만 되는 경우에만 사용
- 런타임 시에만 발생하는 문제를 만들 가능성이 있다.
- 접근 지시자를 의도적으로 무시할 수 있어 보안적 이슈

---

</div>
</details>

<br>

<details>
<summary>다이나믹 프록시</summary>

<br>

<image src='./img/dynamic_proxy.jpg'>

- 프록시 단점 : 모든 인터페이스 직접 구현, 부가 기능 코드 중복 가능성

<br>

### 다이나믹 프록시 
- 모든 요청을 리플렉션 정보로 변환해 InvocationHandler 구현 객체의 invoke() 메서드로 위임하는 방식
- 객체에 대한 Reflection을 사용하기 때문에 성능 하락의 원인이 됨.

---

</div>
</details>

<br>

<details>
<summary>JDK Dynamic Proxy vs CGLIB</summary>

<br>

작성중 ....

</div>
</details>

<br>

<br>
<br>

## Spring

<details>
<summary>빈 생명 주기</summary>

<br>
- 빈 인스턴스화 및 의존성 주입
- 스프링 인지 검사 (빈이 application context를 알아야하는 경우)
- 빈 생성 콜백 메서드 호출
- 빈 소멸 메서드 호출


---

</div>
</details>

<br>

<details>
<summary>Spring MVC</summary>

<br>
웹 개발 시 M,V,C 단의 관심사를 분리함으로써 독립적으로 개발.
변경 라이플 사이클이 다르다!


- Controller : HTTP 요청을 받아 파라미터 검증. 비즈니스 로직 실행, 뷰에 전달할 데이터를 조회하여 모델에 저장
- Model : 뷰에 출력할 데이터를 저장. 뷰가 필요로 하는 데이터를 모두 모델에 담아 전달해줌으로써 비즈니스 로직이나 데이터 접근을 모른 채 화면을 렌더링하는 일에 집중
- View : 모델에 담겨 있는 데이터를 사용하여 화면을 그리는 일에 집중


---

</div>
</details>

<br>

<br>
<br>

## DATABASE

<details>
<summary> 트랜잭션 개념과 성질 </summary>

<br>

- ACID

### 1. 원자성 (actomicity)
- 트랜잭션이 DB에 모두 반영 or 전부 미반영
- `하나의 트랜잭션 안에 있는 연산이 전부 수행되거나 수행되지 않는다. (커밋 or 롤백)`

### 2. 일관성 (Consistency)
- 데이터베이스의 무결성 보장
- 트랜잭션의 작업 처리 결과는 항상 일관성
- `송금 전후 모든 금액의 데이터 타입은 정수형`

### 3. 독립성 (Isolation)
- 둘 이상의 트랜잭션이 동시에 병행 실행되고 있을 때, 어떤 트랜잭션도 다른 트랜잭션 연산에 끼어들 수 X

### 4. 영속성 (Durability)
- 트랜잭션이 성공적으로 완료되었으면 결과는 영구적으로 반영

---

</div>
</details>

<br>

<details>
<summary> 격리 수준 </summary>

<br>

**Read Uncommited**
- 아직 커밋중인 데이터를 다른 트랜잭션이 읽는 것을 허용

**Read Commited**
- 커밋된 데이터를 다른 트랜잭션이 읽는 것을 허용

**Repeatable Read - MYSQL**
- 처음 읽기 시점을 기억하여 도중 다른 트랜잭션이 커밋되어도 읽는 값에 변화되지 않음을 보장
  - Phantom Read 
    - 한 트랜잭션 중간에 insert를 발생시키는 트랜잭션이 발생
    - 현 트랜잭션이 update를 하게 될 경우 일관되지 않은 결과가 발생

**Serializable**
- 다른 트랜잭션 접근 불가

---

</div>
</details>

<br>

<details>
<summary> 트랜잭션 전파 속성 </summary>

<br>

| 속성 | 설명 | 
|---|---|
| REQUIRED | 부모 트랜잭션이 존재한다면 부모 트랜잭션으로 합류, 없다면 새로운 트랜잭션 생성 |
| REQUIRES_NEW | 무조건 새로운 트랜잭션 생성. 각각의 트랜잭션 롤백 시 서로 영향 x |
| MANDATORY | 부모 트랜잭션에 합류. 부모 트랜잭션이 없는 경우 예외 발생 |
| NESTED | 부모 트랜잭션이 존재하면 중첩 트랜잭션 생성. 롤백 시 중첩 트랜잭션 시작지점까지 롤백, 부모 트랜잭션이 없는 경우 새로운 트랜잭션 생성 |
| NEVER | 트랜잭션 생성 X, 부모 트랜잭션이 존재하면 예외 발생 |
| SUPPORTS | 부모 트랜잭션이 있다면 합류. 진행중인 부모 트랜잭션이 없다면 트랜잭션 생성 X |
| NOT_SUPPORTED | 부모 트랜잭션이 있다면 보류. 부모 트랜잭션이 없다면 트랜잭션 생성 X |

---

</div>
</details>

<br>

<details>
<summary> 트랜잭션 vs @Transactional </summary>

<br>

- 트랜잭션 : 데이터베이스의 상태를 변화시키기 위해 수행하는 작업의 단위
- @Transactional : 애플리케이션 단의 트랜잭션. 비즈니스 로직을 수행하는 트랜잭션

---

</div>
</details>

<br>

<details>
<summary> Connection Pool </summary>

<br>

- DB와 연결된 Connection을 미리 만들어 Pool 속에 저장 => 필요한 경우 Connection을 Pool에서 꺼내 쓰고 다시 반환
- Connection은 인증 과정으로 인한 생성 비용이 크고, 매 생성마다 메모리를 사용하기 때문에 connection 수를 제어하지 않는 경우 메모리 부족 현상이 발생할 수 있다.
- Connection Pool을 이용해 미리 연결된 스레드 풀을 이용해 connection 개수를 관리하고 연결 비용과 메모리 부족 문제를 해결한다.

### 동작 과정

1. 어플리케이션 실행
2. DB와 연결된 Connection 객체들을 미리 생성해 Pool에 저장
  - DB와 Connection을 맺어놓고 있는다.
3. DB 요청 시 Pool에 저장된 Connection 객체를 가져와 DB에 접근
4. 처리가 끝나면 다시 Pool에 Connnection 객체를 반납

---

</div>
</details>

<br>

<details>
<summary> FailOver </summary>

<br>

- MHA(Master High Availiability) 사용
  - Master DB 장애 발생 시 자동으로 failover를 수행하여 Slave DB를 Master DB로 승격시켜 서비스 다운 타임을 최소화하는 솔루션

---

</div>
</details>

<br>

<details>
<summary> MYSQL 쿼리 동작 과정 </summary>

<br>

1. Connection Pool에서 객체를 가져옴
2. SQL Parser : 쿼리 문장 👉 토큰 분리 👉 트리 구조
3. Optimizer : 인덱스 유무, 데이터 편향 정보 등을 참고해 최적화된 실행 계획을 찾아 수립
4. Exution Egine : 실행계획대로 각 핸들러에게 요청해 받은 결과를 다른 핸들러의 요청 입력으로 연결하는 역할
5. handler(storage engine) : 실행 엔진 요청에 따라 데이터 👉 디스크 저장/읽기


---

</div>
</details>

<br>

<details>
<summary> Storage Engine </summary>

<br>

### InnoDB

- pk 인덱스 자동 생성
  - 클러스터링으로 쓰기 성능이 저하되지만, 읽기 요청이 많은 경우 유리
- mvcc 기능 : 버퍼 풀과 언두로그
- undo 로그 (변경 이전 데이터)와 리두 로그(커밋된 데이터)
- 레코드 단위 Lock 👉 사실 인덱스 Lock
  - 인덱스가 성씨일 경우 '박'을 검색하면 모든 '박' 레코드가 Lock
  - 성씨 + 이름으로 인덱스를 설정하여 레코드 잠금을 달리 할 수 있다.
- 버퍼 풀 : 쓰기 작업 지연, 일괄 처리, 페이지 단위로 테이블 데이터를 관리 (LRU)
- adaptive hash index
  - 자주 사용되는 데이터 값을 내부에서 판단하여 상황에 맞게 해시 생성

### MyISAM

- 클러스터링, 트랜잭션, 외래키 지원 X
- 키 캐시 사용


---

</div>
</details>

<br>

<details>
<summary> MVCC </summary>

<br>

- 하나의 레코드에 대해 2개의 버전 유지
- 필요에 따라 어느 데이터가 보여지는 지 여러 상황에 따라 달라지는 구조
- **잠금을 사용하지 않는 일관된 읽기 제공**
- **[격리수준]Uncommited** : 변경된 데이터 상태 반환
- **[격리수준]Commited 이상** : undo 영역의 데이터 반환
- commit 시 버퍼풀의 내용을 영속화 / rollback 시 undo 영역으로 복구

---

</div>
</details>

<br>

<details>
<summary> 인덱스 튜닝 </summary>

<br>

- 조회 성능 향상 목적
- 대량의 데이터에서 소량의 데이터를 탐색하기 위해 랜덤 I/O 횟수 최소화

### 종류
- 수직적 탐색
  - 스캔 시작 지점을 탐색
  - 인덱스 스캔 과정의 비효율성 최소화
- 수평적 탐색
  - 찾고있는 데이터 탐색
  - 랜덤 I/O 횟수 최소화
- **랜덤 액세스(수평적탐색) 최소화 튜닝이 중요**

---

</div>
</details>

<br>

<details>
<summary> 논/클러스터링 인덱스 </summary>

<br>

### 클러스터링 인덱스
- 실제 DB의 데이터 파일에 정렬이 되어있는 상태로 디스크에 저장
- 선택 범위가 30% 이내일 때 효율적

### 넌클러스터링 인덱스
- 실제 DB의 데이터 파일에 정렬되지 않은 상태로 디스크에 저장
- leaf level까지 찾아간 뒤 랜덤 I/O를 통해 데이터 추출
- 선택 범위가 3% 이내일 때 효율적

</div>
</details>

<br>

<br>

## KOTLIN

<details>
<summary> val, var의 차이점 </summary>

<br>

var은 일반적인 변수로, 여러번 할당될 수 있는 변경가능한(mutable) 변수이다.
val은 정적인 변수로 한번만 초기화할 수 있고 변경불가능한(immutable) 변수이다.


</div>
</details>

<br>