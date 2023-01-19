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
  
  ---

## git 주의사항

1. 현재 위치를 잘 확인한다.
2. repo(master 있는게 리포야)안에서 repo를 만들지 않는다.
 3) 이미 git init 을 한 곳 안에
 4) 하위 폴더를 만들고
 5) 그 하위 폴더에서 git init을 하지 않는다.
* master 떠있으면 init 제발 X
1. 홈(~)에서 git init을 하지 않는다.(리포 밖에 리포를 만드는 것이기 때문)
만약에 이렇게 했다면 다시 폴더로 만들어줘야 한다.
1. (지금은) github에서 직접 수정하지 않는다.

## git recommendation
1. 커밋 메시지는 짧지만 내용은 담아서
2. 모든 Repo(프로젝트)는
	1. 리포 최상단(.git/과 같은 위치에)
	2. README.md
	3. .gitignore 담고 있도록 한다.

양은 많지만 올라갈 필요없는, git이 관리하지 않도록 하는 gitignore

---

## git 사용법

1. git init : 폴더를 리포로 초기화 (저장소로 활용할 디렉터리로 이동한 다음, 이 코드를 작성하면 git 저장소를 생성(초기화)할 때 사용한다.)
2. git add : 작업 디렉토리 상의 변경 내용을 스테이징 영역에 추가하기 위해서 사용한다. 기록할 때까지 변경분을 모아놓는다.
3. git commit : git add보다 확실히 명시적으로 기록을 남긴다.
4. git status : 작업 디렉토리와 스테이징 영역 상태 확인한다.
5. git log : 가장 최근의 커밋이 가장 먼저 나오고, 지난 히스토리를 시간순으로 조회한다.
6. git config --global user.name "name" : 사용자 이름 설정
7. git config --global user.email "email@com" g: 사용자 이메일 설정
8. git remote add [<name>> <URL>] : remote(원격 저장소)에 URL 추가, origin이라고 하면 URL을 의미하는 것이다.
9. git push <name> <branch> : 내 로컬 디렉토리로부터 <name>,흔히 origin이라는 remote repo로 보낸다. origin의 master브랜치에 푸쉬.

    ex)
    git branch -m master

    git push origin main

10. git clone <URL>
    :URL은 저장소의 주소(github에 저장소를 만들고 이 저장소를 클론해서 작업하기 때문). 
    - remote는 이 명령으로 원격 저장소를 연결/확인 하는 것이라면, clone은 github repo에 있는 내용을 내 컴퓨터에 복제하는 명령
11. git pull : 원격 저장소에 있는 프로젝트 내용을 가져온다.
    - git clone은 로컬 저장소의 내용이 원격 저장소의 내용과 일치하고 프로젝트에 처음 투입될 때 사용돼야 하는 명령어라면, git pull은 원격 저장소의 내용을 가져와서 현재 브랜치와 합치는 것도 해주기 때문에 최신 코드로 업데이트 할 수 있다.
  ---

  ## 요약

```
- README 파일 & .gitignore 생성
 touch README.md .gitignore

- gitignore.io 에 접속하여 필요한 내용 ctrl c v

- README & .gitignore 파일 add(tracking)
 git add . (add 다음에 꼭 띄어쓰기!)

- commit
 git commit -m 'first commit'

- github에서 원격 저장소 직접 생성

- 생성한 원격 저장소 등록  (origin 은 별명)
 git remote add origin <URL>

- 등록된 저장소 확인
 git remote -v

- 지금까지의 commit들 모아서 push
 git push origin master
```


### 명령어 정리

1. 처음 리포 초기화 시점에 1회 입력

```
 git init 
```

2. 작업 후 스테이징

```
 특정 파일만 add 할 때
 git add <filename>
 현재 폴더 전체를 add 할 때
 git add .
```

3. 커밋 진행

```
 메시지는 짧고 정확하게
 git commit -m 'MESSAGE'
```


4. 모니터링 명령어

```
 현재 Working Dir 과 Stage 상황 확인 (주기적으로 확인하자!)
 git status

# commit 로그 
$ git log     
# commit 로그 짧게
$ git log --oneline
```

5. github 에 원격 저장소 생성하기 (github site에서 `New Repository`)
  
6. 원격 저장소(remote repo) 추가하기

```sh
$ git remote add origin <URL>
```

7. 원격 저장소 확인하기

```sh
$ git remote -v
```

8. 원격 저장소에 지금까지의 commit 들 PUSH 하기

```sh
$ git push origin master
```

9. 새로운 컴퓨터에서 기존 원격 저장소 복제하기
```sh
 git clone <URL>
```

10. 원격 저장소의 내용 받아오기
```
 git pull origin master
 ```

 |상황|명령어|
|--|--|
|집에서 새로운 프로젝트 시작|`$ mkdir project`|
|프로젝트 폴더로 이동|`$ cd project`|
|리포 초기화|`$ git init`|
|README, .gitignore 생성|`$ touch README.md .gitignore`|
|파일 스테이징|`$ git add .`|
|커밋|`$ git commit -m 'first commit'`|
|원격저장소 생성|github 사이트에서 진행|
|원격 저장소 등록|`$ git remote add origin <URL>`|
|원격 저장소 PUSH|`$ git push origin master`|
|다른 컴퓨터에서 원격저장소 복제|`$ git clone <URL>`|
|작업|`add`, `commit`|
|귀가 직전|`$ git push origin master`|
|집 도착 이후|`$ git pull origin master`|
|작업|`add`, `commit`|
|작업 종료|`$ git push origin master`|
|다른 컴퓨터에서 반복|`$ git pull origin master`|