# Flyway (Spring Boo)

### 형상관리란?

---

변경사항을 체계적으로 추적, 통제한다는 것이다. 이 말은 어떤 문서나 파일이 변경 되었을 때 변경된 내역을 기록하였다가 나중에 이를 찾아봐야 할 경우, 변경 원인과 변경 사항을 확인해야 할 경우에 대한 관리를 말한다.

### Flyway?

---

Flyway는 DB 형상 관리 도구이다. DB의 스키마나 데이터를 관리할 때, 버전 관리나 마이그레이션 등의 일을 자동화할 수 있다. 

Flyway를 사용하면 DB 관리가 편리해진다. 자동화로 휴먼에러(개발자의 실수)가 줄어들고, DB의 상태를 일관되게 유지할 수 있다는 장점이 있다. 

> 간단한 구조와 명확한 규칙으로 이루어져 있다.
 DB에 적용할 SQL 스크립트를 파일로 작성하고, Flyway가 이를 적용하고 실행하는 방식이다.
> 

### Flyway 적용 방법

---

1. Flyway 라이브러리를 추가한다.

```groovy
dependencies {
    implementation 'org.flywaydb:flyway-core'
    implementation "org.flywaydb:flyway-mysql"
    implementation 'org.springframework.boot:spring-boot-starter-data-jpa'
    runtimeOnly 'mysql:mysql-connector-java'
}
```

1. 설정 파일 추가

```yaml
spring:
  flyway:
    enabled: true
    baseline-on-migrate: true
    baseline-version: 1
```

- `sprig.flyway.enabled` : Flyway 를 사용할지 여부 (기본값 true)
- `spring.flyway.baseline-on-migrate` : Flyway의 버전 관리를 시작하기 전에 이미 존재하는 DB와 테이블을 어떻게 처리할지 설정 (기본값 false)
- `spring.flyway.baseline-version` : Flyway가 초기화되지 않은 DB에 마이그레이션을 적용할 때 버전 설정 (기본값 1)

1. DB에 적용할 마이그레이션 파일을 작성한다. 

마이그레이션 파일은 `v(숫자)__(파일이름).sql` 형식으로 작성한다.

> DB에 기존 데이터가 존재할 경우 db/migration 위치에 반드시 스크립트 파일이 있어야 한다. 특별한 변동 없이 기존 테이블과 데이터를 유지하고자 해도 빈 script 를 작성해야 한다.
> 

참고자료

[Spring Boot Flyway 적용기](https://mindybughunter.com/spring-boot-flyway-%EC%A0%81%EC%9A%A9%EA%B8%B0/)