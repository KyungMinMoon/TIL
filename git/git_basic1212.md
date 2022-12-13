# git 기초

## git의 개념과 학습 이유
- Git : 분산형 버전 관리 시스템
- 몇 명이서 작업을 하더라도 동료들과 나는 같은 페이지에서 각자 수정사항을 업로드할 수 있고, 서로 주고받는 중에 일어나는 충돌을 최소화할 수 있다.
### VCS(Version Control System)
- 파일의 변화를 추적하고 관리하는 시스템

### Working Directory
- 현재 위치의 디렉토리
  
### Stage
- 현재 수정한 파일을 곧 commit할 것이라고 표시한 상태

### Commit
- 파일 및 폴더의 코드 변화(추가/변경)를 기록한다.
  
## git 사용법


오늘 배운거
1. git init : 저장소로 활용할 디렉터리로 이동한 다음, 이 코드를 작성하면 git 저장소를 생성(초기화)할 때 사용한다.
2. git add : 작업 디렉토리 상의 변경 내용을 스테이징 영역에 추가하기 위해서 사용한다. 기록할 때까지 변경분을 모아놓는다.
3. git commit : git add보다 확실히 명시적으로 기록을 남긴다.
4. git status : 작업 디렉토리와 스테이징 영역 상태 확인한다.
5. git log : 가장 최근의 커밋이 가장 먼저 나오고, 지난 히스토리를 시간순으로 조회한다.
6. git config --global user.name "name" : 사용자 이름 설정
7. git config --global user.email "email@com" : 사용자 이메일 설정
8. git remote add [<name>> <URL>] : remote(원격 저장소)에 URL 추가, origin이라고 하면 URL을 의미하는 것이다.
9. git push <name> <branch>
10. git clone <URL>
11. git pull