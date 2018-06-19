---
layout: post
title: BaekJoon-no.1707 이분그래프
categories:
- Algorithms
tags: algorithms programming dfs bfs
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/1707)

체감 난이도(1~5) : 3.0

### 풀이

DFS를 이용한 그래프 분류  
check[x] == 0, 1, 2 로 구분해서 집합을 나눈다. 그 후, 인접한 것들의 집합이 같은지, 아닌지로 판별한다.


```c
int dfs(int x,int color){ 
	check[x] = color;
	for(int i =0;i<a[x].size();i++){
		int y = a[x][i];
		if(check[y] == 0 ) 
		{
			if(dfs(y,3-color)==-1)
				return -1; 
		}
		else if(check[x] == check[y])
			return -1; 
	}   
	return 0;
}
```

### 배운 점

- dfs에서 check 배열 활용하는 법을 익힘
