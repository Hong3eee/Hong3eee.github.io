---
layout: post
title: BaekJoon-no.21562156
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/2156)

체감 난이도(1~5) : 2.5

### 풀이

N번째에 어떤 상태가 올 지 고려.  
0 - 안마실 때, 1 - 연속으로 1 잔째를 마실 때, 2 - 연속으로 2 잔째를 마실 때로 나눠서 생각한다.  

```c
for(int i=1;i<n+1;i++)
{   
	d[i][0] = max(d[i-1][0],max(d[i-1][1],d[i-1][2]));
	d[i][1] = d[i-1][0] + p[i];
	d[i][2] = d[i-1][1] + p[i];
} 
```

### 배운 점

- -
