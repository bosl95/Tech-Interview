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
| | 많은 문자열 연산 시 효율적 | 많은 문자열 연산시 효율적|
| | equals 메서드 오버라이딩 X | StringBuffer - 스레드 동기화 기능 |

- 스레드 동기화를 뺀 StringBuilder의 성능이 더 빠르다.


---

</div>
</details>

<br>

<details>
<summary>HashMap/HashTable/ConcurrentHashMap</summary>

<br>


---

</div>
</details>

<br>


<br>