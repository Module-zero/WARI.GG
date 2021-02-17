# GIT FLOW

- 처음 git 을 만들면 master 브랜치가 생긴다
- master 브랜치는 배포가 가능한 버전들만 올리는 브랜치라고 보면된다
- 따라서 실제 개발을 할 때는 master 브랜치에서 develop 브랜치를 생성하여, **develop 브랜치에서 개발을 진행한다.**
- github 상에서 develop 브랜치를 default 브랜치로 설정한다
- **develop 브랜치에서 각 이슈에 해당하는 임시 브랜치를 생성하여 작업한 후, 다시 develop 브랜치로 통합(merge)한다**
- develop 브랜치로 통합할 때는, github 에서 pull request 을 올려 팀원들의 동의를 얻어 merge 한다
<br/><br/>

## CASE 1.&nbsp; 수정사항을 github 에 올려야 할 때

> 서버 코드 수정 작업을 완료해서 이를 github 상에 올려야하는 상황이라고 가정해보자


### **1. git checkout develop + git checkout -b server_issue**
     - 반드시 develop 브랜치에서 임시 브랜치를 생성해야 하므로 먼저 develop 브랜치로 이동한다.
     - server_issue 라는 이름의 임시 브랜치를 생성한 뒤 해당 브랜치로 checkout(이동)한다.

### **2. git status, add ..., commit ...**
     - 로컬상에 있는 server_issue 브랜치에 변경사항이 적용된다. 이 외의 브랜치에는 변경사항이 적용되지 않는다.

### **3. git push origin server_issue**
     - github 상에 변경사항이 적용되어있는 server_issue 라는 새로운 브랜치가 생성된다.

### **4. pull request 요청**
     - pull request 를 요청해서 github 상에서 develop 브랜치에 server_issue 브랜치를 merge 한다.
     - 그리고 github 상에서 server_issue 브랜치를 삭제하면 github 상에서의 작업은 끝난다.

### **5. git branch -D server_issue + git pull origin develop**
     - 이제 로컬에 있는 server_issue 브랜치도 역할을 다했으니 삭제한다.
     - 그리고 github 상에 develop 브랜치를 로컬로 끌고 옴으로서 로컬의 develop 브랜치도 최신상태를 유지하도록 한다.
<br/>

## CASE 2.&nbsp; 수정 사항을 github 에서 내려받아야 할 때
