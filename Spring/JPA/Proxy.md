# Proxy

JPA의 프록시는 엔티티의 **지연로딩을 구현**하는데 사용됨

- 엔티티 간의 관계에서 지연로딩은 연관된 엔티티를 실제로 필요한 시점에 로딩하는 기법
- JPA 프록시는 지연로딩을 위해 사용되고 엔티티 클래스를 상속받아 프록시 객체를 생성함

### 프록시 Proxy

---

- JPA에서 엔티티의 프록시는 엔티티 객체를 대신하여 DB의 실제 행에 접근하는 가벼운 객체
- 프록시는 실제 엔티티 클래스를 상속받아 생성되며 **엔티티의 모든 필드와 메소드** 가지고 있음
  - 하이버네이트가 내부적으로 상속받아 만들어짐
- 사용하는 입장에서는 진짜 객체인지 프록시 객체인지 구분할 필요 없음
- 그러나 프록시는 실제 데이터를 지연로딩을 통해 가져올 수 있음

### 프록시 초기화

---

- JPA에서 프록시 객체가 **실제 엔티티 데이터를 로딩하는 동작**
  프록시는 실제 데이터를 로딩하지 않고 가벼운 객체로 유지되다가, 프록시 객체를 통해 실제 데이터에 접근하려 할 때 DB에서 데이터를 가져와 프록시 객체를 실제 엔티티 객체로 변환
- **지연로딩 :** 프록시 초기화는 지연로딩을 위해 사용됨. 연관된 엔티티의 데이터를 실제로 필요한 시점에 가져오는 것을 지원
- **Lazy Initialization :** 프록시 객체 자체는 실제 데이터를 가지고 있지 않음, 필요한 데이터를 실제로 접근할 때만 가져옴
- **프록시 객체 활용 :** 프록시 객체 사용 시에는 실제 엔티티와 동일한 방식으로 사용, 프록시 객체의 메소드를 호출하거나 속성에 접근하면 프록시 초기화가 발생하여 실제 데이터를 가져옴

---

```java
//예시 코드
@Entity
public class Author {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    @OneToMany(mappedBy = "author", fetch = FetchType.LAZY) // 지연 로딩 설정
    private List<Book> books;

    // getters and setters
}

@Entity
public class Book {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String title;

    @ManyToOne
    @JoinColumn(name = "author_id")
    private Author author;

    // getters and setters
}
```

- Author 와 Book 의 일대다 관계 설정

```java
//예시 코드
public class Main {

    public static void main(String[] args) {
        EntityManagerFactory emf = Persistence.createEntityManagerFactory("my-persistence-unit");
        EntityManager em = emf.createEntityManager();

        em.getTransaction().begin();

        Author author = new Author();
        author.setName("John Doe");
        em.persist(author);

        Book book1 = new Book();
        book1.setTitle("Book 1");
        book1.setAuthor(author);
        em.persist(book1);

        em.getTransaction().commit();
        em.close();

        // 이 시점에서는 아직 프록시가 로딩되지 않음
        em = emf.createEntityManager();
        em.getTransaction().begin();

        Author loadedAuthor = em.find(Author.class, author.getId());

        // 지연 로딩된 엔티티를 접근하는 시점에서 프록시가 초기화되어 데이터를 가져옴
        List<Book> books = loadedAuthor.getBooks();

        for (Book book : books) {
            System.out.println("Book Title: " + book.getTitle());
        }

        em.getTransaction().commit();
        em.close();

        emf.close();
    }
}
```

- loaderAuthor.getBooks()를 호출하는 시점에서 프록시가 초기화되어 작가의 책 데이터가 가져와짐 → 지연로딩 실현
