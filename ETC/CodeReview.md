# Code Review

**코드리뷰?** 작성한 코드를 다른 사람들이 검토하고 피드백을 전달하고 다시 작성자가 반영하는 과정

### 이루어져야 할 것들

---

- 버그, 성능 문제가 발생할 수 있는 가능성 제시
- 다른 해결 방법에 대한 의견 제시
- 정해진 표준 준수하고 있는지 확인 → 많은 사람들의 개발 결과물이 일관됐는지 확인
- 기술적인 지식과 노하우 공유
- 맥락과 히스토리를 누가봐도 인지할 수 있도록 개발되고 설명되는지 체크

### 좋은 코드리뷰를 위해서

---

- 괜히 내가 리뷰해서 일정이 딜레이 되진 않을까?
- 내 말이 기분 나쁘지 않을까?
- 저 코드는 고쳐줬음 하는데… 저 사람도 자기만의 스타일이 있는거겠지… 등등

→ 이러한 부분을 해소하기 위한 방법

1. **코딩 컨벤션 맞추기**

IDE 의 기능을 이용하여 코딩 컨벤션을 일관되게 함으로써 코드에 대한 가독성을 높일 수 있음

1. **작은 PR 만들기**

왜? 만들어낸 기능, 클래스가 많다면 리뷰하기 어렵고 시간 투자 많이 해야하기 때문

- feature 하나를 개발할 때 기능별 세부 feature로 구분하여 개발 진행
- ex) 하나의 PR에는 1000줄 이하의 코드, 1개의 서브 기능 별 1PR 등

### Pn 룰

---

리뷰어가 본인이 남긴 리뷰에 대한 무게감을 표현하는 방식으로 사용

- P1 : 꼭 반영 부탁
- P2 : 적극적으로 고려 부탁
- P3 : 웬만하면 반영 부탁
- P4 : 반영해도 좋고 넘어가도 좋음
- P5 : 그냥 사소한 의견임..

**일정에 리뷰 및 피드백 반영기간 포함하기!!**

잘못된 업데이트 하나, 변경사항 하나가 큰 영향을 미칠 수 있기 때문에,

리뷰를 하고 이를 반영하는 행위에 대한 중요성을 키웠으면 함
