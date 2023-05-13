**컬렉션 프레임워크?** 다수의 데이터를 쉽고 효과적으로 처리할 수 있는 클래스의 집합

—> 데이터를 저장하는 자료구조와 데이터를 처리하는 알고리즘을 구조화하여 클래스로 구현

---

### 주요 인터페이스

[List 컬렉션 클래스](https://www.notion.so/List-6d8eebf67a754a58821ff55ff88eec1a)

[Set 컬렉션 클래스](https://www.notion.so/Set-30f6c8c9e5d84510900679ff130a2955)

[Map 컬렉션 클래스](https://www.notion.so/Map-82c35f41fa1b4f3db22b1052feb9dd97)

List, Set 인터페이스는 모두 Collection 인터페이스 상속, 하지만 Map 인터페이스는 별도 정의

---

### **상속관계**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3af3c016-a5d1-4fff-b48e-97128928e71c/Untitled.png)

<E>,<K,V>는 프레임워크 구성하는 모든 클래스가 제네릭으로 표시되어 있음을 나타냄

---

### 컬렉션 클래스

**컬렉션 클래스?** 컬렉션 프레임워크의 인터페이스를 구현한 클래스

List, Set, Map 인터페이스 중 하나 구현

---

### 컬렉션 인터페이스

컬렉션을 다루는데 가장 기본적인 동작 정의, 메소드로 제공

ex) boolean add(E e), void clear(), int size(), boolean isEnpty(), Object[] toArray() 등

- Collection은 인터페이스, Collections는 클래스 차이
