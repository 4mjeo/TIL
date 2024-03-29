# Web Socket

두 프로그램 간의 데이터를 교환하기 위한 **통신방법** 중 하나이다.

**Html5(현재 인터넷 환경)**에서 많이 사용한다.

### 웹소켓 특징

**1 양방향 통신**

- 데이터 송수신을 동시에 처리 가능하다.
- 클라이언트와 서버가 서로 원할 때 데이터 주고받을 수 있다.
- 일반적인 http통신은 클라이언트가 요청 할때만 서버가 응답하는 단방향 통신이 가능하다.

**2 실시간 네트워킹**

- 웹 환경에서 연속된 데이터를 빠르게 노출할 수 있다.
- 여러 단말기에 데이터를 빠르게 교환할 수 있다.

---

### 동작 방법

(UTF-8 인코딩 방식 사용)

**1 핸드쉐이크**

client server

http(80) / http(443) ←——————→ http(80) / http(443)

**2 데이터 전송**(핸드쉐이크 완료)

client server

ws(80) / wss(443) ←——————→ ws(80) / wss(443)

**3** **closing framework**를 주고 받으며 종료

---

### 웹소켓 프로토콜 특징

- 최초 접속에서만 http에서 핸드쉐이킹을 하기 때문에 http header 사용한다.
- 웹소켓 위한 별도의 포트는 x, 기존 포트 사용한다.
- 프레임으로 구성된 메세지라는 단위로 송수신한다.
- 메세지는 **텍스트**와 **바이너리**만 가능하다.

---

### 웹소켓 한계

- HTML5 이전의 기술로 구현된 서비스에서 웹소켓처럼 사용할수 있게하는 기술이다.(Socket.io,SockJS)
- 문자열들 송수신 밖에 하지 못한다.(해독은 앱에..)
- HTTP는 형식 지정 o→ 해석 가능 but 웹소켓은 형식지정 x → 쉽게 해석 x
- STOMP
  1 채팅 통신을 위한 형식 정의
  2 HTTP와 유사하게 정의되어 해석하기 편리
  3 보통 웹소켓 위에서 사용

**STOMP 프레임구조**

```java
COMMAND
header1:value1
header2:value2

BodyBodyBody^@
```
