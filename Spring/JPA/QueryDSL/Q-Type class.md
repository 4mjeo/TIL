# Q-Type class

**Q-Type class**는 QueryDSL 설정을 성공적으로 마치면 @Entity가 붙은 클래스를 찾아 **자동 생성**됨

ex) @Entity가 붙은 Userjava 클래스가 있다면 QUserjava 파일이 자동으로 생성됨

- Q-Type class들은 QueryDSL을 사용하여 메소드 기반으로 쿼리를 작성할 때 도메인 **클래스의 구조를 설명**해주는 **메타데이터 역할**을 함
- **쿼리의 조건을 설정**할 때 사용됨

### 기본 Q-Type

---

**Q 클래스 인스턴스 사용하는 방법**

- 별칭 직접 지정

```java
QMember qMember = new QMember("m");
```

같은 테이블을 Join 하는 경우, 서브쿼리를 사용하는 경우가 아니라면 잘 사용 안 함

- 기본 인스턴스 사용

```java
QMember qMember = QMember.member;

//QMember 클래스 파일에 다음과 같은 코드 만들어짐
public static final QMember member = new QMember("member1");
```
