---
layout: post
title: BaekJoon-no.11726
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/11726)

체감 난이도(1~5) : 2.5

### 풀이

N 번째 칸을 채우는 경우를 생각하면 두 가지 경우가 나올 수 있다.  
m[n-1] 까지 구한 경우, 마지막 세로 직사각형 하나를 끼우는 경우,  
m[n-2] 까지 구한 경우, 마지막 가로 직사각형 두 개를 끼우는 경우로 구분해서 푼다.  

```c
int func(int n){ 
	if(m[n]>0)
		return m[n];
	if(n<3)
		return m[n];

	m[n] = (func(n-1) + func(n-2))%10007;

	return m[n];
}

```

### 배운 점

- 모든 경우의 수를 하나씩 쓰다보면 패턴이 보이는 쉬운 경우
## - 그러나 그건 요행에 가깝다고 생각함. 풀이처럼 m[N]에 들어가는 경우의 수를 몇 가지로 나누어서 생각하도록 연습하자!!
