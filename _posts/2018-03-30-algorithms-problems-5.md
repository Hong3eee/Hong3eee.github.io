---
layout: post
title: BaekJoon-no.1463
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/1463)

체감 난이도(1~5) : 2

### 풀이

DP 문제의 전형.  
DP의 기본 속성인 1.겹치는 부분문제 2.작은 문제의 답으로부터 구할 수 있는  답 을 충족하고 있다.  
그렇다면 작은 문제를 배열등을 이용하여 차근차근 풀어나가면 쉽게 해결 가능.

```c
if(n%3 == 0)
	tmp = func(n/3);
if(n%2 == 0)
	tmp2 = func(n/2);

tmp3 = func(n-1);

m[n] = min(min(tmp,tmp2),tmp3) +1; 

return m[n];
```

### 배운 점

- DP 문제의 전형적인 유형 파악
- 메모이제이션 패턴의 적용 방법 파악
- 모든 DP 문제를 이러한 패턴으로 풀 수가 있따!!!

