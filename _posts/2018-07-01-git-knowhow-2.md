---
layout: post
title: GIT 02. Git의 원리
categories:
- etc
tags: Git
commnets: true
---

- [지옥에서 온 GIT, 생활코딩](https://opentutorials.org/course/2708)

강의의 공부내용을 정리해서 올립니다.  
깃에 대해 항상 헷갈려하는 모두와 나 자신을 위해.

### git add 의 원리

git 은 어떤 파일을 저장할 때, 파일의 이름이 달라도 내용이 같다면 같은 오브젝트 파일을 가르킨다.

### object 파일명의 원리

git은 파일의 내용을 가지고 sha-1 이라는 해쉬알고리즘을 이용해서 값을 얻는다. 그 후 이 값을 이용해 오브젝트 디렉토리 밑에 디렉토리, 파일을 만든다.  
즉, 파일의 내용을 가지고 해쉬를 만들게 되므로 파일의 내용이 같다면 같은 파일을 가르킨다.

### commit 의 원리

##### object 의 형태
- blob -> 파일의 내용을 담고있다
- tree -> 파일의 이름과 파일의 이름이 가지고 있는 내용정보(blob)를 갖고있다
- commit -> 커밋에 관련한 정보들의 모음집. parent ( 상위 커밋이 뭔지 ), tree, author, committer, commit message 등을 가지고 있다

tree 커밋이 일어난 시점에 작업디렉토리에 있는 파일의 이름과 파일의 이름이 담고있는 내용 정보가 담겨있음

각각의 버전은 그 버전이 만들어진 시점(*커밋*) 의 스냅샷을 트리라는 정보구조를 통해 가지고 있다.

그리고 이 커밋은 그 버전들을 만드는 명령어이다.


### status 의 원리

- index 파일에 적혀 있는 값과 working directory 의 파일 내용이 다르다면 이를 출력해준다.

- 최신 커밋과 현재 index 파일의 내용이 다르다면 정보 출력.
  
git 의 전체적인 flow 는 이러하다.

![git workflow](/img/git_workflow.png)
