# JPA(Java Persistence API)

JPA란 자바 ORM 기술의 표준, 인터페이스의 모음 → 구현체 없음

---

### ORM?

- 클래스와 관계형 DB를 매핑하는 것
- 테이블이 객체로 매핑되어 SQL 작성 필요 없음
- 객체지향적인 코드 작성 가능함

---

### 이유?

- 쿼리 작성 필요 없음 → 코드량 줄어듦
- SQL이 아닌 객체 중심 개발 → 가독성 높아짐, 편리함 유지보수
- 유지보수 편리함(→ SQL 수정 필요 없음)
  ***

### Repository

```java
public interface CrudRepository extends JpaRepository<Crud, Long> {

		List<Crud> findById(Long id)
```

- JpaRepository는 Spring Data JPA가 제공하는 JPA 구현을 위한 인터페이스임

→ CRUD 쿼리 실행 가능
