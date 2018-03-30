---
layout: post
title: BaekJoon-no.1158
categories:
- Algorithms
tags: algorithms programming queue
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/1158)

체감 난이도(1~5) : 1.5

### 풀이

큐를 이용하여 푼다.  
입력으로 들어오는 M-1 만큼 front에서 pop해서 back에 푸쉬를 하고 M 번째 값을 출력한다.

```c
for(int i=0;i<N;i++){
	for(int j =0;j<M-1;j++){
		q.push(q.front());
		q.pop();
	}
	...
}
```

### 배운 점

- 큐 기본 사용법에 대한 숙지
