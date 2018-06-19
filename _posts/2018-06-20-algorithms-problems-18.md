---
layout: post
title: BaekJoon-no.1260 DFS와 BFS
categories:
- Algorithms
tags: algorithms programming dfs bfs
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/1260)

체감 난이도(1~5) : 1.0

### 풀이

DFS BFS 기본 풀이
	


```c
void dfs(int x){ 
	check[x] = true;
	printf("%d ",x);
	for(int i =0;i<v[x].size();i++){
		int y =v[x][i];
		if(check[y] == false)
			dfs(y);
	}   
}

void bfs(int x){ 
	queue<int> q;
	memset(check,false,sizeof(check));
	check[x] = true;
	q.push(x);

	while(!q.empty()) {
		int top = q.front();
		q.pop();
		printf("%d ",top);
		for(int i = 0;i<v[top].size();i++){
			int y = v[top][i];
			if(check[y] == false)
			{
				check[y] = true;
				q.push(y);
			}
		}
	}   
}
```

### 배운 점

- DFS BFS 기본 구현방식 습득  
- 리스트,스택,큐를 이용한 구현방식 습득, 모든 DFS BFS 문제는 이러한 형태이다
