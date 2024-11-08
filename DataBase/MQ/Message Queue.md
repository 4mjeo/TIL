# Message Queue

MSA 아키텍처로 많은 개발이 이루어지고 있는 현재, 핵심 역할을 하는 `Message Queue`에 대해 알아봅시다.

## 메세지 지향 미들웨어 (MOM)

---

> 메세지 지향 미들웨어란? 응용 소프트웨어 간의 비동기적 데이터 통신을 위한 소프트웨어이다.
> 

메세지 API를 통해 각 분산되어 있는 애플리케이션의 다리역할을 함으로써 데이터를 교환할 수 있게 하는 시스템이다.
메세지를 통해 여러 분산되어 있는 시스템 간의 Connector 역할로 결합도를 낮추고, 이들이 서로 실시간 비동기식 데이터를 교환할 수 있도록 하는 소프트웨어이다.

`메세지 큐` 가 `MOM`을 구현한 시스템이다.

## 메세지 큐 (MQ)

---

**Queue?** 선입선출 구조를 가진 자료구조이다. `Message`는 순차적으로 `Queue`에 들어오고 `Queue`는 순차적으로 들어오는 `Message`를 받아서 갖고 있다가 하나씩 순서에 맞게 전달한다.

여기서 메세지를 발행하고 전달하는 부분을 producer 라고 하며, 메세지를 받아서 소비하는 부분을 consumer 라고 한다.
메세지 큐는 producer 와 consumer 의 메세지 전달 역할을 하는 매개체이다.

## 메세지 브로커 vs 이벤트 브로커

---

메세지 큐에서 데이터를 운반하는 방식에 따라 메세지 브로커, 이벤트 브로커로 나눈다.

> 메세지큐는 메세지가 송수신되는 하나의 통신 통로라고 한다면, 브로커는 메세지 큐에 메세지를 넣고 중개하는 역할을 한다. *즉, 메세지 큐와 브로커는 다른 개념이다.*
> 
- 메세지 브로커

`Producer`가 생산한 메세지를 메세지 큐에 저장하고, 저장된 메세지를 `consumer`가 가져갈 수 있도록 한다.
메세지 브로커는 consumer가 메세지 큐에서 데이터를 가져가면, *짧은 시간 내에 메세지 큐에서 삭제된다.*

ex) RabbitMQ, ActiveMQ, AWS SQS, Redis

- 이벤트 브로커

이벤트 브로커도 메세지 브로커의 역할을 할 수 있다. 하지만 메세지 브로커는 이벤트 브로커의 기능을 하지는 못한다.

이벤트 브로커가 관리하는 데이터를 이벤트라고 하며 `consumer`가 메세지 큐에서 데이터를 가져가게 되면 짧은 시간 내에 메세지가 삭제되는 것과 달리, 이벤트 브로커에서는 `consumer`가 *소비한 데이터를 필요한 경우 다시 소비할 수 있다.*

또한 메세지 브로커보다 대용량의 데이터를 처리할 수 있다.

ex) Kafka

## MQ의 장점

---

- 비동기 - 큐에 넣기 때문에 나중에 처리할 수 있다.
- 낮은 결합도 - 애플리케이션과 분리할 수 있다.
- 탄력성 - 일부가 실패 시 전체에 영향을 받지 않는다.
- 과잉 - 실패할 경우 재실행이 가능하다.
- 보증 - 작업이 처리된 것을 확인할 수 있다.
- 확장성 - 다수의 프로세스 들이 큐에 메세지를 보낼 수 있다.

## MQ의 단점

---

- 큐가 가득 차서 더 이상 큐에 메세지를 저장할 수 없는 상황에는 메세지를 다른 곳에 보존하거나 버린다.
- 메세지 큐의 크기는 생각보다 작기 때문에 송신측이 수신측보다 빠르면 문제가 발생할 수 있다.

## 언제 MQ를 사용할까?

---

- 서버 부하가 많은 작업
    
    이미지 처리, 비디오 인코딩, 대용량 데이터 처리와 같은 작업을 할 때 처리할 작업을 MQ에 넣고 서버는 자신이 처리할 수 있는 양에 따라서 작업을 처리할 수 있다.
    
- 부하 분산 (MQ를 통해 부하분산 처리도 가능하다.)
    
    처리할 데이터가 많아져도 각 서버는 자신의 처리량에 맞게 태스크를 가져와서 처리한다.
    
- 데이터 손실 방지
    
    MQ에서 가져온 태스크를 일정 시간이 지나도록 처리했다고 다시 MQ에 알려주지 않으면 MQ는 이 태스크를 다시 큐에 넣어서 처리한다. 즉, 데이터 저장이 가능하다.
    

## MQ의 종류

---

- **ActiveMQ (JMS)**
    - MOM을 자바에서 지원하는 표준 API이다. JMS는 다른 자바 애플리케이션끼리 통신이 가능하지만 다른 MOM의 통신은 불가능하다. (AMQP, SMTP 같은…)
    - ActiveMQ의 JMS 라이브러리를 사용한 자바 애플리케이션끼리 통신이 가능하다.
    - 하지만 다른 자바 애플리케이션의 JMS와는 통신할 수 없다.

- **RabbitMQ**
    - RabbitMQ는 AMQP(Advanced Message Queue Protocol)을 구현한 오픈소스 메세지 브로커이다.
    - AMQP는 MQ를 오픈 소스에 기반한 표준 프로토콜이다. 프로토콜만 맞다면 다른 AMQP를 사용한 애플리케이션끼리 통신이 가능하다.
    - 플러그인을 통해서 SMTP, STOMP 프로토콜의 확장이 가능하다.
    - AMQP는 아래 방식 중 하나로 메세지 전달을 보장한다.
        - At-Most-Once: 각 메세지는 한번만 전달되거나 전달되지 않는다.
        - At-Least-Once: 각 메세지는 최소 한번 이상 전달을 보장한다.
        - Exactly-Onec: 각 메세지는 딱 한번만 전달된다.
    - Exchange가 producer로부터 메세지를 받고 queue에 전달한다. queue는 consumer에게 메세지를 전달한다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FCTWxw%2FbtrqMvOz41o%2F0wCCFT4TekiWBeoeEjEX01%2Fimg.png)

- **Apache Kafka**
    - 높은 처리량을 요구하는 실시간 데이터 피드 처리나 대기 시간이 짧은 플랫폼을 제공하는 것을 목표로 하며 TCP 기반 프로토콜을 사용한다.
    - 클러스터를 중심으로 producer와 consumer가 데이터를 push하고 pull하는 구조를 가진다.
    
    ![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FdaLAbi%2FbtrqQedM2kR%2FCs3UVw6cdkSJ6e8UbtK8Y1%2Fimg.png)
    
    - 특징
        - Publisher / Subscriber 모델
        - 고가용성, 확장성, 디스크 순차 저장 및 처리, 분산 처리
    - 카프카는 내구성이 뛰어난 메세지 저장소로, 필요에 따라 이벤트 스트림을 재생할 수 있다.
    - 대용량의 실시간 로그 처리에 특화되어 설계되어 기존 범용 메세징 시스템 대비 TPS가 우수하다.
    - AMQP 프로토콜이나 JMS API를 사용하지 않고 단순한 헤더를 지닌 TCP 기반의 프로토콜을 사용하여 오버헤드를 감소시켰다.
    - 다수의 메세지를 batch 형태로 broker에게 한번에 전달할 수 있어 TCP/IP 라운드 트립 횟수를 줄일 수 있다.
    - 기존의 메세징 시스템에서는 broker가 consumer에게 메세지를 push 해주는 방식인데, Kafka는 consumer가 broker로부터 직접 메세지를 가지고 가는 pull 방식으로 동작한다.
  
> 정리하자면, 대용량 분산 시스템이 필요하면 `Kafka`를, 그 외에는 `Queue` 기능에서 신뢰성과 안정성을 보장하는 `ActiveMQ` 혹은 `RabbitMQ`을 사용하면 될 것이다.
>