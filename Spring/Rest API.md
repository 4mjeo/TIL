# Rest API

### Rest(Representational State Transfer)

---

- HTTP URI 를 통해 자원을 명시하고 HTTP Method를 통해 해당 자원에 대한 CRUD를 적용하는 것
- 자원의 이름으로 구분하여 해당 자원의 상태를 주고 받는 것 → **자원의 표현에 의한 상태 전달**

ex) DB의 학생 정보가 자원일 때 ‘students’를 자원의 표현으로 정함

- 웹의 기존 기술과 HTTP 프로토콜을 그대로 활용

→ **웹의 장점 최대한 활용 가능**한 아키텍쳐 스타일

### 장단점

---

- HTTP 프로토콜의 표준을 최대한 활용하여 여러 장점들을 가져갈 수 있게 해줌
- Rest API 사용을 위한 별도의 인프라 구축 필요 없음
- 의도하는 바 쉽게 파악 가능
- 서버&클라이언트 역할 명확하게 분리

- 표준이 존재하지 않음
- 메소드 4가지 밖에 없음

### Rest 구성 요소

---

**1 자원: URI**

- 모든 자원에 고유한 ID가 존재하고 이 자원은 Server에 존재
- 자원을 구별하는 ID는 HTTP URI임
- 클라는 URI를 통해 자원을 지정하고 해당 자원 상태에 대한 조작을 Server에 요청

**2 행위: HTTP Method**

- HTTP 프로토콜 Method 사용

**3 표현**

- 클라이언트가 자원의 상태에 대한 조작을 요청하면 Server는 적절한 응답을 보냄
- Rest에서 하나의 자원은 **JSON, XML**, TEXT, RSS 등 여러 형태로 나타남

### 특징

---

**1 Server - Client**

- 자원이 있는 쪽이 Server, 요청하는 쪽이 Client
- 서로 간 의존성 줄어듦

**2 Stateless(무상태)**

- HTTP 프로토콜이 Stateless이기 때문에 Rest API도 무상태성
- 클라이언트의 context를 Server에 저장하지 않음
- Server는 각각의 요청을 완전 별개의 것으로 인식하고 처리

**3 Cacheable(캐시 처리 가능)**

- 웹 표준 HTTP 프로토콜을 그대로 사용함 → 웹에서 사용하는 기존의 인프라 그대로 활용
- 대량의 요청을 효율적으로 처리하기 위해 캐시가 요구됨
- 캐시 사용으로 응답 시간이 빨라지고 Rest Server 트랜잭션 발생하지 않음 → 전체 효율 향상

4 **Layered System(계층화)**

- 클라는 Rest API Server만 호출함
- Rest Server는 다중 계층으로 구성 가능함

### Rest API

---

**REST 기반으로 서비스 API를 구현한 것**

### 특징

---

- REST 기반으로 시스템을 분산해 확장성, 재사용성을 높여 유지보수 및 운용을 편리하게 함
- HTTP 표준을 기반으로 구현함 → HTTP를 지원하는 프로그램 언어로 Client&Server 구현 가능

### RESTful

---

**RESTful?** REST라는 아키텍쳐를 구현하는 웹 서비스를 나타내기 위해 사용되는 용어

- REST API를 제공하는 웹 서비스를 ‘RESTful 하다’

**목적?**

- 이해 및 사용이 쉬운 REST API를 만드는 것
