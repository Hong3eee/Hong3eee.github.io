---
layout: post
title: BaekJoon-no.4963 섬의 개수
categories:
- Algorithms
tags: algorithms programming dfs bfs
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/4963)

체감 난이도(1~5) : 2.5

### 풀이

DFS BFS 어떤 방식으로 풀어도 상관없는 문제.  
BFS를 이용해, 좌표를 갖는 `queue<pair<int,int>> q` 큐를 사용해 품


```c
void bfs(int i,int j){ 
	group[i][j] = group_num; //방문
	q.push(make_pair(i,j));
	while(!q.empty()){
		int first = q.front().first;
		int second = q.front().second;
		q.pop();

		for(int k=0;k<8;k++)    //방향 배열 사용
		{
			int x,y;
			x = first+dx[k];
			y = second+dy[k];
			if( (x>=0 && x<h) && (y>=0 && y<w) )
			{
				if(arr[x][y] == 1 && group[x][y] == 0)
				{
					group[x][y] = group_num;
					q.push(make_pair(x,y));
				}
			}
		}
	}   
}
```

### 배운 점

- 연결된 요소를 찾는 문제. 빈출유형
- 좌표를 다룰 때 pair 구조체 사용법
- + 좌표 다룰 때 배열과 같이 사용했는데 x,y좌표와 배열의 몇차원 원소에 넣어야 하는지가 너무 헷갈렸다. `ex) arr[y][x] or arr[x][y]` 이에 대한 기준을 마련하자.
