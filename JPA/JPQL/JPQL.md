# JPQL

- **Java Persistence Query Language**
- 엔티티 객체를 조회하는 객체지향 쿼리(테이블 대상이 아님)
- SQL과 비슷한 문법이며 JPQL은 결국 SQL로 변환됨

### 특징

---

1. **객체지향 쿼리 언어**

- 객체와 엔티티 관계를 중심으로 쿼리 작성 가능

1. **연관 관계와 조인 지원**

- 엔티티 사이의 관계를 이용해 DB 조인 표현 가능

→ 복잡한 쿼리 간결하게 작성 가능

1. **특정 DB에 종속적이지 않음**

- JPQL은 SQL을 추상화 한것임

→ DB 사용에 있어 자유로움

### 기본 문법

```java
//예시
String jpql = "select m from Member as m where m.name = 'coco'";
```

SQL과 거의 동일하지만 몇가지 다른 점이 있음

---

**1) 대소문자 구분**

- 엔티티와 속성은 대소문자 구분함(엔티티 Member, 속성 member)
- SELECT, FROM, WHERE 같은 JPQL 키워드는 구분 안함

**2) 엔티티 이름**

- Member는 클래스가 아닌 엔티티 이름 → 엔티티 이름은 @Entity(name = “abcd”)로 설정 가능
- name 속성을 생략하면 기본값 사용(클래스 이름)

**3) 별칭 사용**

- 엔티티의 별칭은 필수로 명시해야함(select m from Member m)
- 별칭 명시하는 **AS** 키워드는 생략 가능

### TypeQuery & Query

---

- 쿼리 객체 TypeQuery는 반환값이 명확할때, Query는 불명확 할때 사용함

```java
// 반환 타입이 Member 클래스로 명확
	TypedQuery<Member> typedQuery =
		em.createQuery("select m from Member m", Member.class);

	// 반환 타입이 username, id로 불명확
	Query query =
		em.createQuery("select m.username, m.id from Member m");
```
