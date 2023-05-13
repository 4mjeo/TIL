# 제네릭

제네릭? 데이터 타입을 일반화하는것

사용할 내부 데이터 타입을 컴파일 시에 미리 지정하는 방벙

---

**장점**

1 클래스나 메소드 내부에서 사용되는 객체의 타입 안정성 높일수 있음

2 반환값에 대한 타입 변환 및 타입 검사에 들어가는 노력 줄일수 있음

---

**선언 및 생성**

```java
class MyArray<T> {

    T element;

    void setElement(T element) { this.element = element; }

    T getElement() { return element; }

}
```

‘T’를 타입변수라고 하고, 임의의 참조형 타입 의미 → 메소드의 매개변수나 반환값으로도 사용가능

```java
MyArray<Integer> myArr = new MyArray<Integer>();
```

(Integer 타입 사용예시) 제네릭 클래스 생성시, 사용할 실제 타입을 명시하면, 타입변수가 실제타입으로 반환되어 처리

---

\*자바에서는 타입변수 자리에 사용할 실제 데이터 타입을 바로 명시 불가 → wrpper 클래스 사용

**제네릭 제거**

컴파일된 calss 파일에는 어떠한 제네릭 타입도 명시되지 않음
