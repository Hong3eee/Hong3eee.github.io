---
layout: post
title: GIT 03. Branch??
categories:
- etc
tags: Git
commnets: true
---

- [지옥에서 온 GIT, 생활코딩](https://opentutorials.org/course/2708)

강의의 공부내용을 정리해서 올립니다.  
깃에 대해 항상 헷갈려하는 모두와 나 자신을 위해.

### branch 만들기


`git branch` - 브랜치의 목록을 볼 때

`git branch "new branch name"` - 브랜치를 생성할 때

`git branch -d` - 브랜치를 삭제할 때

`git branch -D` - 병합하지 않은 브랜치를 강제로 삭제할 때

`git checkout "전환하려는 브랜치 이름"` - 브랜치를 전환할 때

`git checkout -b "생성하고 전환할 브랜치 이름"` - 브랜치를 생성 후 전환


### branch 정보 확인


`git log (--branches) (--graph) (--decorate) (--oneline)`

`--branches` - 모든 브랜치의 로그 확인

`--graph` - 브랜치의 계층관계를 명확히 나타나게 해줌

`--decorate` - 브랜치 명 까지 표시해줘서 쉽게 확인할 수 있게 해줌

`--oneline` - 한 줄로 표시

- HEAD - 현재 체크아웃 된 브랜치

`git log "비교할 브랜치 명 1".."비교할 브랜치 명 2"` - 브랜치 간에 비교할 때

`git diff "비교할 브랜치 명 1".."비교할 브랜치 명 2"` - 브랜치 간의 코드를 비교 할 때 


### branch 병합


exp => master 로 병합하려면?
  
master 로 checkout 후, git merge exp!

```
hong3@ubuntu:~/gitfth$ git log --graph --decorate --branches --oneline 
*   5b8b904 (HEAD -> master) Merge branch 'exp'	//이 시점에서 병합, master는 exp, master에서 생성한 모든 커밋을 합쳐놓은 상태가 된다
|\  
| * e8249ed (exp) 7	// 그래프에서 *에 위치 중요. exp에서는 오른쪽 라인에 *이 있는 커밋만 가지고 있다. 즉, 커밋 8,6 은 기록하지 않았다.
| * 0a0183c 5
* | 587a7fd 8
* | 1c2fb01 6
|/  
* b8ba985 4
* d674a94 3
* 1f727b3 2
* 4a145d0 hi
```

### Fast foward vs Merge commit

#### - Fast foward ?

브랜치를 나눈 후(A 브랜치), 마스터 브랜치에서 아무일도 하지 않고, A 브랜치를 머지하고 싶을때 사용됨.  
즉 바로 A 브랜치가 가르키고 있던 커밋으로 바로 가게 된다.

- commit 을 생성하지 않음


![branch1](/img/basic_branching_4.png)

---

![branch2](/img/basic_branching_5.png)


---


#### - Merge commit ?

브랜치를 나눈 후(B 브랜치), 마스터 브랜치에서 새로운 커밋을 추가한 후, B 브랜치를 머지하고 싶을때 사용됨.  
master 와 B 브랜치의 공통의 조상을 찾음, 그 후 C4와 C5 커밋을 합친다.

- merge commit을 생성한다


![merge1](/img/basic_merging_1.png)

---

![merge2](/img/basic_merging_2.png)


### branch 병합 시 충돌해결

- merge 할 때, 다른 브랜치들이 같은 파일을 다뤘어도 서로 수정한 위치가 다르다면 자동으로 합쳐진다!

- 그러나 같은 파일의 같은 부분을 다루는 경우 충돌이 일어난다!

```
hong3@ubuntu:~/gitfth$ git merge exp
Auto-merging common.txt
CONFLICT (content): Merge conflict in common.txt
Automatic merge failed; fix conflicts and then commit the result.
// common.txt 에서 충돌이 났다고 알려준다.

hong3@ubuntu:~/gitfth$ git status	// 충돌 확인
On branch master
You have unmerged paths.
	(fix conflicts and run "git commit")

Unmerged paths:
	(use "git add <file>..." to mark resolution)

		both modified:   common.txt
no changes added to commit (use "git add" and/or "git commit -a")


hong3@ubuntu:~/gitfth$ vi common.txt 
~~~~~~~~common.txt~~~~~~~~~~
<<<<<<< HEAD		// 현재 브랜치의 파일 내용
fucntion a(master)
=======
fucntion a(exp)
>>>>>>> exp 		// merge 하려는 exp 브랜치의 파일 내용
// 이 부분을 수정하여 충돌이 일어나지 않게 해줘야한다. 특수 기호들도 제거할 것. 작업이 끝나면 git add, commit 해서 병합을 완료한다
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

### git stash 

- stash (감추다 , 숨겨두다)

다른 브랜치로 Checkout 해야 하는데 아직 현재 브랜치에서 작업이 끝나지 않은  경우, 커밋을 하기 애매.  
이런 경우 stash 를 이용해 현재 track중인 파일을 임시로 저장해둘 수 있다.   
그 후 브랜치를 이동해서 작업을 끝낸 후, 다시 원래 브랜치로 돌아와서 stash 에 저장해 놓은 내용을 복원할 수 있다.


`git stash` - track 하고 있는 파일, 즉 git add 된 파일을 stash 에 임시로 저장하고 현재 working dir 에서는 없애버리는 명령어.

`git stash list` - stash 된 목록을 보여주는 명령어.

`git stash apply` - stash list 의 가장 상단에 있는 것을 현재 working dir 에 불러온다. cf) apply 한다고 해도 stash list 에서 제거되지는 않는다.

`git stash drop` - stash list 의 가장 상단에 있는 것을 삭제한다.

`git stash pop` - `git stash apply` + `git stash drop`

