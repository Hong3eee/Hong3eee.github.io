---
layout: post
title: GIT 01. 첫걸음
categories:
- etc
tags: Git
commnets: true
---

- [지옥에서 온 GIT, 생활코딩](https://opentutorials.org/course/2708)

강의의 공부내용을 정리해서 올립니다.  
깃에 대해 항상 헷갈려하는 모두와 나 자신을 위해.

### 저장소 생성

- `git init`

.git 디렉토리가 생성되며 여기에 버전정보들이 저장됨.

- `git status`

git 상태에 대한 정보를 뿌려줌.

```
$ git status

Untracked files:
  (use "git add <file>..." to include in what will be committed)

  	f1.txt
```

### 버전 생성

- `git add`

git에게 관리해야 하는 파일이 무엇인지를 알려주는 명령어.

```
$ git add f1.txt

$ git status

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

  	new file:   f1.txt

```

- `git config`

```
git config --global user.name "your name"
git config --global user.email "yout email"
```

버전을 만든 사람에 대한 정보를 설정. ~/.gitconfig 파일에 저장되며 초기에 1번만 실행해주면 된다.

- `git commit (-m commit message)`

add 된 파일들을 버젼으로 만드는 명령어.

### Stage Area

commit 전에 add 를 꼭 해야한다. **선택적으로** 파일을 버전에 포함시키기 위해서. 

commit 전, add 된 파일들이 있는 곳을 Stage Area 라고 한다.  
여기서 commit을 하게되면 repository로 파일이 옮겨진다.

### 변경사항 확인하기

버전을 만든 것에 대한 효용 ??

- 첫 번째, 차이점 과거의 어느 시점의 내용을 알 수 있다.
- 두 번째, 과거로 돌아갈 수가 있다.

이러한 특성을 이용, 수정된 내용을 추적해서 문제해결을 한다!

- `git log -p`

로그에서 출력되는 버전 간의 차이점을 출력하고 싶을 때

- `git diff '버전 id'..'버전2 id'`

버전 간의 차이점을 비교할 때

- `git diff`

git add 하기 전과 add 한 후의 파일 내용을 비교할 때.  
commit 을 하기 전에 마지막 비교를 제공하는 명령어.

### 과거의 버전으로 돌아가기

**Reset** vs **Revert**

- `git reset --hard '버전 id'`

버전 id 로 돌아가는 명령.

- `git revert '버전 id'`

버전 id 의 커밋을 취소한 내용을 새로운 버전으로 만든다.

