# Directory Structure

### 계층형 디렉토리 구조

```java
com
	↳ example
		↳ cmdproject
			↳ config
			↳ controller
			↳ domain
			↳ repository
			↳ service
			↳ security
			↳ exception
```

- 스프링 각 웹 계층들을 대표하는 클래스, 디렉토리를 기반으로 패키징함

**스프링 웹 계층**

- Web Layer : 사용자의 요청과 이에 대한 응답 반환의 전반적인 처리가 일어나는 영역
- Service Layer : Web Layer와 Repository Layer 사이에서 실질적인 애플리케이션 비즈니스 로직이 일어나는 영역
- Repository Layer : DB에 접근 및 통신하는 영역

**장점**

- 전체적인 구조 빠르게 파악 가능

**단점**

- 각 패키지에 클래스들이 너무 많이 모임
- 하나의 패키지 안에 서로 의존하는 수많은 클래스들이 모여있어 유지보수가 힘듦

### 도메인형 디렉토리 구조

```java
com
	↳ example
		↳ cmdproject
			↳ domain
				↳ account
					↳ controller
					↳ dto
					↳ entity
					↳ exception
					↳ repository
					↳ service
				↳ user
					↳ controller
					↳ dto
					↳ entity
					↳ exception
					↳ repository
					↳ service
			↳ global
				↳ auth
				↳ common
				↳ config
				↳ error
				↳ infra
				↳ util
```

- 스프링 웹 계층이 아닌 도메인 별로 패키지 분리 가능하도록 함

**장점**

- 관련된 코드들이 응집해 있음
- 각 도메인들이 서로 의존하는 코드가 적도록 설계하기 적합해서 코드 재활용성 향상됨

**단점**

- 프로젝트에 대한 이해도가 낮을 경우 전체적인 구조 파악 어려움
