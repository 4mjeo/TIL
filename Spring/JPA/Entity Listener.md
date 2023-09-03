# Entity Listener

### Entity Listener

---

- 엔티티의 변화를 감지하고 테이블의 데이터를 조작하는 일
- 이전에는 컬럼값이 수정되는 것에 반복된 코드를 추가해야 했음

→ 개발자가 직접 코드 추가 → 실수 발생 → **엔티티 리스너**가 해결!

- 미리 정의된 리스너 메소드가 호출되어 동작 실행
- 코드 중복 방지, 유지보수성 향상

### 생명주기 이벤트

---

1. **@PrePersist**

- 엔티티가 저장되기 전에 호출됨 → 엔티티를 DB 에 삽입하기 전에 메소드 실행

1. **@PostPersist**

- 엔티티가 저장된 후에 호출됨 → 엔티티가 DB에 삽입 된 후에 메소드 실행

1. **@PreUpdate**

- 엔티티가 업데이트 되기 전 호출됨 → 엔티티의 데이터 변경 전 메소드 실행

1. **@PostUpdate**

- 엔티티가 업데이트 된 후 호출됨 → 엔티티의 데이터가 DB에 업데이트 된 후 메소드 실행

1. **@PreRemove**

- 엔티티가 삭제되기 전 호출됨 → 엔티티가 DB에서 삭제되기 전 메소드 실행

1. **@PostRemove**

- 엔티티가 삭제된 후 호출됨 → 엔티티가 DB에서 삭제된 후 메소드 실행

### 사용

---

```java
//예시 코드
@EntityListeners(MyEntityListener.class) //이 어노테이션 붙어야 함
@Entity
public class MyEntity {

    @Id
    @GeneratedValue
    private Long id;

    private String name;

    // Getters and setters
}

public class MyEntityListener {

    @PrePersist   //생명주기 메소드 정의
    public void prePersist(MyEntity entity) {
        // 엔티티가 저장되기 전에 실행될 작업
    }
}
```
