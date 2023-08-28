# Git-flow

**flow?** 흐름이라는 뜻으로 “Git을 잘 이용하는 방법론”

### Git flow

---

브랜치를 나누는 방법에 대한 분류 중 하나

브랜치가 5가지로 나뉜다는 특징

- main(maste) : 서비스를 직접 배포하는 역할
- feature(기능) : 각 기능 별 개발하는 역할
- develop(개발) : feature 에서 개발된 내용이 저장되는 역할
- release(배포) : 배포 하기전 내용을 QA(품질검사)하기 위한 역할
- hotfix(빨리 고치기) : main 브랜치로 배포를 하고 나서 버그가 생겼을 때 빨리 고치기 위한 역할

main, develop은 필수 브랜치, 나머지는 유지보수를 목적으로 하는 선택적 브랜치

아래와 같은 방식으로 Git-flow 사용

![git-flow_overall_graph](https://github.com/4mjeo/TIL/assets/129156398/40b84ca1-a335-4cec-891c-e237a05ab97f)

### 진행 과정

---

1. master 브랜치에서 시작
2. 동일한 브랜치를 develop에서도 생성하고 여기서 개발
3. 기능 구현이 필요할 때 feature 브랜치 파서 구현함
4. 완료된 feature 브랜치는 검토 후 다시 develop 브랜치 합쳐짐(Merge)
5. 모든 기능 완료되면 develop 브랜치를 relearse 브랜치로 만듦 → QA 진행
6. 끝나면 release 브랜치를 master 브랜치와 develop 브랜치에 보냄

6-1. master 브랜치에서 버전 추가를 위해 태그 생성 후 배포

1. 미처 발견하지 못한 오류가 있을 경우 hotfixes 브랜치를 만들어 수정 후 수정 배포

### 왜 브랜치를 분류하는**가**

---

**협업 중 브랜치 충돌을 방지하기 위함**

→ feature 브랜치에 코드 작성
