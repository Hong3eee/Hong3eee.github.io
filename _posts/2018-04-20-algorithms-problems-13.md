---
layout: post
title: BaekJoon-no.2579
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/2579)

체감 난이도(1~5) : 1.5

### 풀이

포도주 문제와 거의 유사함.  N번째는 무조건 선택하도록 하는 d 배열을 만들고 그 전에 어떤 경우의 수들이 올 수 있는지 나눠본다.  n-1, n-2, n-3 등에 어떤 경우가 오는지 판별해서 점화식을 세우면 된다.

```c
d[1] = a[1];
d[2] = a[1]+a[2];
for(int i = 3; i<n+1;i++)
{   
d[i] = max(d[i-2]+a[i] , d[i-3]+a[i-1]+a[i]);
}   
```

### 배운 점

- 이전 문제에서 느낀 2차원 dp가 아니라 1차원 dp로 해결했다. 당연한 얘기지만 2차원으로 풀린다.
- 포도주 시식 문제와 거의 비슷해서 매우 쉽게 풀었다.
