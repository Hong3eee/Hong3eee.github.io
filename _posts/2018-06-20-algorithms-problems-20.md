---
layout: post
title: BaekJoon-no.9466 텀 프로젝
categories:
- Algorithms
tags: algorithms programming dfs bfs
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/9466)

체감 난이도(1~5) : 3.5

### 풀이

DFS 를 이용한 사이클 구하는 문제의 변형.  
재귀함수의 인자로 유용한 데이터를 넘긴 후 이를 이용해 값을 구한다.  
check[x] 배열에 어떤 값이 있다면 이미 방문한 노드이므로 (cnt - check[x] = 사이클의 길이) 를 이용해 값을 구함


```c
int dfs(int x,int cnt,int g){
	
	int y = a[x][0];
	
	if(group[y] !=0 && group[y] != g)
		return 0;
	if(check[x] != 0)
		return cnt - check[x];
	
	check[x] = cnt;
	group[x] = g;
	
	return dfs(y,cnt+1,g);
}

```

### 배운 점

- DFS 재귀 함수의 인자로 적절한 데이터를 넘김으로써 문제를 해결할 수 있음을 배움
- 단순히 하나의 check 배열을 쓸 필요는 없다
- 사이클을 이용한 문제 유형 파악, 대부분 이와 비슷하다
