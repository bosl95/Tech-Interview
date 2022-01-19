# 🔥 Tech-Interview

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

<br>