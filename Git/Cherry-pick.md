# Cherry-pick

**git cherry-pick?** 다른 브랜치에 있는 **커밋을 선택**하여 **내 브랜치에 적용**시킬 때 사용

- rebase도 원하는 커밋을 선택 가능하지만 현재 브랜치 위에서만 가능
- 다른 브랜치 커밋을 가져오려면 해당 브랜치를 현재 브랜치로 merge후 rebase

cherry-pick은 같은 내용인 커밋을 여러개 생성함 → **꼭 필요할때만** 진행

### 언제 사용할까

---

- **팀 협업 시**
  - 팀원이 만든 작업을 merge 할때까지 시간이 걸린다면 만든 기능이 있는 커밋만 골라 가져옴
- **버그 수정 시**
  - 기존 기능에서 버그가 발견되었을 때 버그를 패치하기 위해 명시적 커밋을 만들고 해당 커밋만 골라서 master 브랜치에 배포
- **반영되지 않은 손실된 커밋 복원(pr)**
  - pr를 merge하기 전에 닫아버렸을 때, cherry-pick을 사용해 해당 커밋을 가져옴

### git cherry-pick

---

![img1 daumcdn](https://github.com/4mjeo/TIL/assets/129156398/1abd9954-a4c3-43d7-ae09-dff1fd16db48)

- 브랜치 y의 커밋 중 **76ae30ef와 13af32cc만 골라 현재 브랜치인 X에 적용**하고 싶다고 가정

```bash
# 하나씩
$ git cherry-pick 76ae30ef
$ git cherry-pick 13af332cc

# 인라인으로 한꺼번에
$ git cherry-pick 76ae30ef 13af32cc
```

체리픽을 하여 브랜치 x에 적용하면 이전 커밋 수정사항이 x브랜치에 적용됨

![img1 daumcdn](https://github.com/4mjeo/TIL/assets/129156398/3db9a7c7-61de-499d-a065-33f4a488dafa)

브랜치 x로 복사된 상황

### cherry-pick 충돌

---

작업 중이던 파일과 cherry-pick을 통해 가져온 커밋이 동일하여 conflict 발생 가능

- **충돌 해결 후 cherry-pick 진행**

1. 충돌 난 코드를 해결
2. **git add <path>** 명령으로 수정된 코드 등록
3. **git cherry-pick —continue** 명령어로 중지되었던 cherry-pick을 계속 진행

- **cherry-pick 중단**

1. **git cherry-pick —abort** 명령어를 사용해 cherry-pick을 중단하면 이전 상태로 돌아갈 수 있음

### cherry-pick merge

---

merge commit을 cherry-pick 하고 싶다면 다음 명령어 사용

```bash
$ git cherry-pick -m 1 <merge_commit_hash>
```
