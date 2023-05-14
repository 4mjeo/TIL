# Optional

Optional? ‘null일수도 있는 객체’를 감싸는 일종의 Wrapper 클래스 → _NullpointerException_ 문제해결

**Optional 객체 생성**

---

```jsx
Optional<User> result = userRepository.findById(userId);
```

사용예시

```jsx
Optional<String> opt = Optional.ofNullable("자바 Optional 객체");

System.out.println(opt.get());
```

참조변수가 null 이 될 가능성이 있다면, ofnullable() 메소드 사용하여 optional 객체 생성

**ofnullable() 메소드?** null이 아니면 명시된 값이 있는 optional 객체 반환, null이면 비어있는 optional 객체 반환

---

**목적**

if를 이용한 null 값 체크 대체가능

- 코드 가독성 업
- null 값 체크할 필요없기 때문에 실수 낮아짐

---

**자주 사용되는 메소드**

1. orElseGet()

- optional 이 가지고 있는 값이 null 일 경우에만 주어진 함수 실행

1. orElse()

- null 값과 상관없이

1. orElseThrow()

- 저장된 값이 존재하면 그 값 반환, 존재하지 않으면 예외 발생
