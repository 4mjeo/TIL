# NoSql

**NoSql?** 비관계형 데이터베이스(RDBMS 지양)

- 대량의 분산된 데이터를 저장하고 조회하는데 특화
- 스키마 없이 사용가능 하지만 느슨한 스키마 제공하는 저장소

NoSql은 기존 RDBMS 형태의 관계형 DB가 아닌 다른 형태의 저장 기술(**RDBMS 한계 극복** 위함)

- RDBMS 스키마에 맞추어 데이터를 관리해야 한다는 한계 극복

→ **수평적 확장성(scale-out)을 쉽게** 할 수 있다

### 1. Key-Value DB

---

- 데이터가 Key와 Value와 한쌍으로 저장됨
- Key는 Value에 접근하기 위한 용도 , 값은 어떤 형태로든 담을 수 있음
- 간단한 API 제공 → 속도 빠름
- Redis, Riak, Amazon Dyamo DB 등

### 2. Document DB

---

- 데이터가 Key와 Document 형태로 저장
- K-V 모델과 다른점? Value 가 계층적인 형태인 Document로 저장됨
- 하나의 객체를 여러 개의 테이블에 나눠 저장할 필요 없음
- 객체-관계 매핑 필요 없음(→ 객체를 Document 형태로 바로 저장 가능하기 때문)
- 쿼리가 SQL과 다름
- Mongo DB, Couth DB 등

1. **Wide Column DataBase**
2. **Graph DataBase**

### 특징

---

1. **RDBMS와 달리 데이터 간 관계 정의하지 않음**

- RDBMS는 데이터 관계를 외래키 등으로 정의하고 JOIN 연산을 수행할 수 있음
- NoSQL은 JOIN 연산 불가능

1. **RDBMS에 비해 대용량의 데이터 저장 가능**

- 페타바이트 급 대용량 데이터 저장 가능

1. **분산형 구조**

- 여러 곳의 서버에 데이터를 분산 저장해 특정 서버에 장애가 발생해도 데이터 유실 혹은 서비스 중지가 발생하지 않도록 함

1. **고정되지 않은 테이블 스키마**

- RDBMS와 달리 테이블 스키마가 유동적임
- 데이터를 저장하는 칼럼이 각각 다른 이름과 데이터로 타입 갖는 것이 허용됨

### 장단점

---

- 스키마가 없기 때문에 유연하며 **자유로운 데이터 구조**
- **언제든** 저장된 데이터 조정하고 새 필드 추가 가능
- 데이터 분산 용이하고 성능 향상을 위한 **scale-up** 뿐만 아니라 **scale-out** 도 가능

- **데이터 중복 발생**할 수 있음
- 중복된 데이터가 변경될 때 **수정을 모든 컬렉션**에서 해야함
- 스키마가 존재하지 않음 → 명확한 데이터 구조 보장 안함, 데이터 구조 결정 어려움

### 언제 사용할까

---

- 정확한 데이터 구조를 알 수 없고 데이터가 변경/확장 가능성 있을 때
- 데이터 변경될 시에는 모든 컬렉션에서 수정해야함

→ **Update 가 많이 이뤄지지 않는** 서비스

- scale-out 가능함 → DB를 scale-out 해야하는 서비스
