---
layout: post
title: BaekJoon-no.2667 단지번호붙이기
categories:
- Algorithms
tags: algorithms programming dfs bfs
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/2667)

체감 난이도(1~5) : 2.0

### 풀이

DFS 를 이용해 연결된 요소등을 구해서 처리함


```c
void dfs(int i,int j){ 
	group[i][j] = group_num; //방문

	group_cnt++; //각 단지마다 값

	for(int k=0;k<4;k++)    //상하좌우 방문할지 반복문 사용해서 검
	{   
		int x,y;
		x = i+dx[k];
		y = j+dy[k];
		if( (x>=0 && x<n) && (y>=0 && y<n) )
		{
			if(arr[x][y] == 1 && group[x][y] ==0)
				dfs(x,y);
		}   
	}   
}
```

### 배운 점

- 방향 벡터? 배열? 의 활용법 숙지
- 이런 연결된 요소를 찾는 문제는 dfs / bfs 무엇을 풀어도 가능함
