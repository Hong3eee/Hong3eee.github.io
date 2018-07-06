---
layout: post
title: BaekJoon-no.1074 Z
categories:
- Algorithms
tags: algorithms programming divide&conquer
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/1074)

체감 난이도(1~5) : 3.0

### 풀이

분할정복을 이용한 문제.  큰 문제를 쪼개서 좌상, 우상, 좌하, 우하 순으로 재귀문을 돌린다. 좌표의 위치가 재귀문으로 들어온 함수 안에 없다면 방문하지 않고 카운트를 올려준다. 다 방문하게 되면 시간초과.

```c
void solve(int y,int x,int size)
{
	if(y==r && x==c)
	{   
		printf("%d\n",cnt);
		return ;
	}   

	if( !( (y <= r && r <y+size) && (x <= c && c<x+size) ) ) //기저사례
	{
		cnt += size * size;     //건너뛰는 칸들을 더해줌
		return ;
	}
	else
	{   
		int half = size/2;
		//  재귀
		solve(y,x,half);
		solve(y,x+half,half);
		solve(y+half,x,half);
		solve(y+half,x+half,half);
	}
}
```

### 배운 점

- 문제를 풀기 전, 시간복잡도를 예상해보고 어떻게 풀어야할지 생각하는 습관을 기르자. 
- 분할정복 카테고리로 푸는 걸 맞았다고 해도 구현방식에 있어서 시간복잡도를 계산하자. 무턱대고 풀면 시간초과가 뜰 가능성이 높다.
- 결국 분할정복,재귀함수를 이용한 풀이는 문제를 분할하고 분할한 문제에서도 답을 찾는 과정을 함수 내에 코딩하는 것이 전부다.
