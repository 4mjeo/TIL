# QueryDSL

**QueryDSL?** 정적타입을 이용해서 SQL 과 같은 쿼리를 생성할 수 있도록 도와주는 프레임워크

- 하이버네이트 쿼리 언어(HQL)의 쿼리를 타입에 안전하게 생성 및 관리해줌

### 왜 사용하나

---

자바 백엔드 기술은 Spring Boot와 Spring Date JPA를 함께 사용함

→ **하지만** 복잡한 쿼리, 동적 쿼리를 구현하는데 있어 한계 → 이러한 문제해결 **QueryDSL**

- QueryDSL이 등장하기 이전에는 Mybatis, JPQL, Criteria 등 **문자열 형태로 쿼리문을 작성**하여 컴파일 시에 오류 발견하는 것이 불가능 했음
- QueryDSL은 **자바 코드로 SQL 문을 작성 가능**함 → 컴파일 시에 오류를 발생하여 잘못된 쿼리 실행 방지

### JPQL vs QueryDSL

---

**JPQL**

```java
String username = "java";
String jpql = "select m from Member m where m.username = :username";

List<Member> result = em.createQuery(query, Member.class).getResultList();
```

- String 이기 떄문에 개발자 의존적 형태
- 컴파일 시 문법 오류 확인 불가능

**QueryDSL**

```java
String username = "java";

List<Member> result = queryFactory
				.select(member)
				.from(member)
				.where(usernameEq(username))
				.fetch();
```

- 모든 쿼리에 대한 내용이 **함수형태**로 제공됨
- 오류가 존재하면 컴파일 단계에서 확인 가능 → risk 줄어듦

### 장점

---

- 문자가 아닌 코드로 쿼리문 작성
- 컴파일 시에 문법 오류 확인 가능
- 코드 자동 완성 기능 활용 가능(IDE)
- 동적 쿼리 언어 구현 가능
