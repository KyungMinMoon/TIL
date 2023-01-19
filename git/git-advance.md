# Git Advance

## RECAP
mkdir git-advanced/

code git-advanced



untracked file 인지하지 못한 파일

# stage에 올리기
git add README.md
git add .gitignore

# 어떤 상태인지 파악
# git status

git commit -m 'first commit'

git diff 

- 했을 때 $ 안 나오면 Q 누르기

새로 내용을 작성했을 때, 왼쪽에 초록줄이 나온다
그러면 '추가된 줄' 혹은 '수정'이란 신호!


git log --oneline

git log --oneline --graph

ctrl + r : git log --oneline 명령어


git commit -m 'first commit'


alias gl='git log'
alias jn='jupyter notebook



1. Untracked
2. Tracked
   1. Unmodified
   2. Modified
   3. Staged
3. 'git status'
4. '.gitignore'

alias gl='git log'
alias jn='jupyter notebook

git branch b1(브랜치 생성)

git branch 치면 b1 *master 가 나옴

git switch b1
git checkout master(다시 master로 바뀜)


1. FF(+commit X)
2. Automatic Merge (+ commit O)
3. Conflict => Manual commit(+commit 0 but 내가 함)\


git switch -c FIRE

git switch master
