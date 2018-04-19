---
layout: post
title: BaekJoon-no.1912
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/1912)

체감 난이도(1~5) : 2

### 풀이

이 문제 역시 DP의 전형적인 모습을 보여준다.  
N번째에 어떤 선택을 할 수 있는지 나누어서 풀면 쉽게 풀린다.
나의 경우, 2차원의 인덱스가 0일땐 n번째 수를 수열에 포함하지않음, 1일땐 포함한다. 두 가지로 나누어서 풀었다.	

```c
for(int i = 1; i<n+1;i++)
{
	d[i][0] = max(d[i-1][0],d[i-1][1]);
	d[i][1] = max(max(d[i-1][1],a[i-1]) + a[i],a[i]);
}
```

### 배운 점

- 내 풀이는 2차원으로 해결했는데, 다른 소스를 보니 1차원으로도 가능했다.
- 1차원으로 풀 수 있게끔 생각하는걸 연습하자.
