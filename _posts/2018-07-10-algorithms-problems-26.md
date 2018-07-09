---
layout: post
title: BaekJoon-no.2447 별찍기 10
categories:
- Algorithms
tags: algorithms programming divide&conquer
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/2447)

체감 난이도(1~5) : 2.0

### 풀이

분할정복을 이용한 문제.

```c
void solve(int y,int x,int size)
{
	if(size == 1)
	{   
		arr[y][x] = '*';
		return ;
	}   

	int next = size/3;

	for(int i =0;i<3;i++)
		for(int j=0;j<3;j++)
		{
			if(i==1&&j==1) continue;
			solve(y+dx[i]*next,x+dx[j]*next,next);
		}
}
```

### 배운 점

- dx[] 배열을 이용해서 반복문을 이쁘게 코딩하자.
- memset 함수를 이용해 다른 한 조건(이 문제에서는 ' ') 을 처리할 수 있다.
