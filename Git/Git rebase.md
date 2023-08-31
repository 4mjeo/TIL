# Git rebase

**git rebase?** 두개의 공통 Base를 가진 브랜치에서 한 브랜치의 베이스를 다른 브랜치의 최신 커밋으로 브랜치 베이스를 옮기는 작업

→ **베이스 다시 설정**하는 작업

### 장점

---

**1 공유 브랜치의 최신 변경사항을 즉시 반영 가능**

- merge는 브랜치에 대한 변경사항을 바로 대응 어려움
- rebase 사용하면 남이 올린 커밋들의 수정사항을 내 브랜치에 바로 반영 가능

- **최신 커밋을 반영하면서 작업을 해야할 때 사용**

**2 커밋이력을 남기지 않으므로 Commit History가 깔끔해짐**

- merge 사용하여 최신 이력 가져오면 복잡하고 어려운 commit history
- rebase history는 깔끔하고 직관적인 History로 프로젝트 관리 가능

- git flow 사용할 때 Rebase and Merge 전략으로 깔끔한 History로 작업 가능
