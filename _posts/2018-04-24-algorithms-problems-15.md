---
layout: post
title: BaekJoon-no.2133 타일 채우기
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/2133)

체감 난이도(1~5) : 2

### 풀이

타일의 마지막 경우에 올 수 있는 블록들을 생각해보자.  
가로로 3개인 것, 세로로 1개 가로로 1개인 경우 2가지. 총 3가지 경우가 나온다.  그런데 이게 전부가 아니라 4칸씩 , 6칸씩 .. 2n 칸씩 추가로 생기는 경우가 1가지 나온다.  이 까지 고려하여 dp로 풀어주면 쉽게 풀린다.


```c
for(int i =1;i<N+1;i++)
{
	if(i%2 == 1)
	{
		d[i] = 0;
		continue;
	}
	d[i] = d[i-2];
	for(int j=1;j*2<=i;j++)
	{
		d[i] += 2*d[i-j*2];
	}
}
```

### 배운 점

- 눈에 쉽게 보이는 경우 말고도 더 있을 수 있음에 유의할 것.
