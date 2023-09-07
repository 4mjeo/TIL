# Spring Bean

**: 스프링 컨테이너가 관리하는 자바 객체(POJO)**

- 사용자가 new 연산으로 직접 객체를 생성하고 메소드 호출함
- IoC 가 적용된 경우에는 객체의 생성과 제어권을 Spring에게 넘김

→ **spring에 의하여 관리당하는 자바 객체 == Bean**

### 스프링 컨테이너

---

- 스프링 빈의 생명주기를 관리하며 생성된 스프링 빈들의 추가적인 기능을 제공함
- Ioc, DI 원리가 적용됨
- **제어의 흐름을 외부에서 관리**하게 됨(객체 생성, 소멸)

### 빈 등록하기

---

1. **컴포넌트 스캔**

```java
// 빈으로 등록할 클래스
@Component
public class AService {
    // ...
}

// 패키지 스캔 설정
@Configuration
@ComponentScan(basePackages = "com.example")
public class AppConfig {
    // ...
}
```

- 자동으로 빈 스캔하고 등록
- **@Component** 로 클래스를 빈으로 선언하고 **@ComponentScan**로 스캔할 패키지 지정
- @Controller, @Service, @Repository, @Configuration은 @Component의 상속을 받음

→ 컴포넌트 스캔 대상

2. **XML 설정**

```xml
//빈 등록 클래스
<bean id="myService" class="com.example.MyService">
    //나머지,,,
</bean>
```

- XML 기반의 스프링 설정 파일로 빈 정의 및 등록
- <bean> 요소를 사용하여 각 빈의 정의를 등록하고 이 파일을 스프링 컨테이너에 로드함

3. **Java Config**

```java
@Configuration
public class AppConfig {
    @Bean
    public MyService myService() {
        return new MyService();
    }
}
```

- Java 클래스로 빈 정의 및 등록
- @Configuration 으로 설정 클래스를 등록하고 **@Bean** 으로 빈 정의

### @Bean vs @Component

---

**@Bean**

- 개발자가 컨트롤 불가능한 외부 라이브러리들을 Bean 으로 등록하고 싶은 경우
- 메소드 또는 어노테이션에 붙일 수 있음

**@Component**

- 개발자가 직접 컨트롤 가능한 클래스들의 경우
- 클래스 또는 인터페이스 단위에 불일 수 있음
