# ApplicationEventPublisher

## ApplicationEventPublisher?

---

- spring 에서 어노테이션을 기반으로 이벤트 처리를 지원한다.
- 직접 publisher, listener를 커스텀해서 기능을 구현할 수 있다.
- 옵저버 패턴을 활용한다.
  - 옵저버패턴? 행위자, 관찰자가 존재한다. publisher와 관찰하는 observer가 있다.
  - 언제 사용할까? 객체 → 다른 객체에게 메세지 알릴 수 있어야 하고, 객체끼리 결합되는 것을 방지할 때 옵저버 패턴을 사용한다.

### Flow

---

1. 이벤트가 발생하면 applicationEventPublisher 가 이벤트를 받는다.
2. Event를 EventMultiCaster에게 전달한다.
3. EventMultiCaster는 각 Listner들에게 broadcasting 하듯 이벤트를 뿌린다.
4. 각 Listner들은 자신의 파라미터를 확인하여 이벤트 타입과 맞지 않으면 무시하고, 맞으면 실행시킨다.

예제

```java
//이벤트 클래스 생성
@Getter
public class AlarmEvent {
    private final Alarm alarm;

    public AlarmEvent(Alarm alarm) {
        this.alarm = alarm;
    }

    public static AlarmEvent from(Alarm.AlarmType alarmType, User target, User from) {
        return new AlarmEvent(Alarm.builder()
                .alarmType(alarmType)
                .targetUser(target)
                .fromUser(from)
                .build());
    }
}
```

```java
//이벤트 핸들러 생성
@Component
public class AlarmEventHandler {
    private final AlarmRepository alarmRepository;

    public AlarmEventHandler(AlarmRepository alarmRepository) {
        this.alarmRepository = alarmRepository;
    }

    @EventListener
    @Async
    public void createAlarm(AlarmEvent event) {
        alarmRepository.save(event.getAlarm());
    }
}
```

- 발행한 이벤트를 핸들링할 이벤트 핸들러를 만든다.
- 스프링이 관리하도록 빈 등록을 해주고(@Component), @EventListner을 활용하여 해당 메서드가 리스너 역할임을 명시해준다.
- 파라미터에 있는 이벤트로 해당 리스너에게 전달된 이벤트인지 아닌지 구분한다.

```java
//이벤트 발행
@Service
@RequiredArgsConstructor
public class CommentService {
	private final CommentRepository commentRepository;
    private final PostRepository postRepository;
    private final UserRepository userRepository;
    private final ApplicationEventPublisher publisher;

	@Transactional
    public CommentCreateResponseDto createComment(CommentCreateRequestDto commentCreateRequestDto,
                                                  Integer postId, String userName) {
        Post post = findPost(postId);
        User user = findUser(userName);

        Comment comment = commentCreateRequestDto.toEntity(user, post);
        commentRepository.save(comment);

        // 내 게시물에 내 댓글을 알람 저장 x
        if (!post.getUser().getUserName().equals(userName)) {
            publisher.publishEvent(AlarmEvent.from(NEW_COMMENT_ON_POST, post.getUser(), user));
        }
        return CommentCreateResponseDto.from(comment);
    }
}
```

### ApplicationEventPublisher 의 한계

---

- 스프링이 제공해주는 이벤트 기능으로, 스프링 빈으로 동작한다.

→ 외부 시스템과의 연동이 불가능하다.

- 또한 다른 서버로 이벤트를 전송할 수 없으니 MSA 구조처럼 각 도메인 마다 서버가 분리되어 있는 경우는 사용 불가능하다. 그래서 Kakfa와 RabbitMQ와 같은 메세징 큐 소프트웨어를 사용한다.
