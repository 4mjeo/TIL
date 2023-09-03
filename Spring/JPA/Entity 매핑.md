# Entity 매핑

- 객체와 테이블 매핑 : @Entity, @Table
- 기본키 매핑 : @Id
- 필드와 컬럼 매핑 : @Column
- 연관관계 매핑 : @ManyToOne, @JoinColumn, @OneToMany, @ManyToMany

### 1. @Entity

---

- JPA를 사용해서 테이블과 매핑할 클래스에 붙여야 함
- 기본 생성자 필수, 저장할 필드에 final 키워드 사용 못함

### 2. @Table

---

- 엔티티와 매핑할 테이블 지정함(생략하면 엔티티 이름 = 테이블 이름)

### 3. @Column

---

- 객체 필드를 테이블 컬럼에 매핑함
- column 대한 속성 정의 가능(name, nullable 등)

### 4. @Id

---

- 기본키 필드를 나타낼 때 사용함
- 모든 엔티티는 하나 이상의 기본키를 가져야 함
