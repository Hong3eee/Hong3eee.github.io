---
layout: post
title: STL queue 사용법
categories:
- Algorithms
tags: algorithms data-structure STL
comments: true
---

큐 Queue

### 정의

- 한쪽에서는 자료를 넣기만 다른 한쪽에서는 자료를 뺄 수만 있는 자료구조
- 큐의 begin 에서는 pop 만, end 에서는 push만 일어난다.
- FIFO(First In First Out)

### 사용법

```c++
#include <queue>

int main(){

	queue<Type> q;

	q.push(~~);
	q.pop();
	q.size();
	q.empty();
	q.front();
	q.back();

	return 0;
}
```

- push() : data를 큐에 삽입, 큐의 size는 +1 이 된다
- pop() : 큐의 가장 위에 있는 data를 큐에서 삭제, size는 -1
- empty() : 큐가 비어있는지, 아닌지 확인. 비어있을시 true 반환
- size() : 큐의 현재 사이즈를 반환
- front() : 큐의 front를 리턴. front 데이터가 삭제되지는 않음
- back() : 큐의 back을 리턴 back 데이터가 삭제되지는 않음


