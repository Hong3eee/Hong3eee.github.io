---
layout: post
title: BaekJoon-no.2146 다리 만들기
categories:
- Algorithms
tags: algorithms programming dfs bfs
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/2146)

체감 난이도(1~5) : 3.0

### 풀이

BFS를 이용, 각 섬들을 넘버링 한 후, 각 섬들에서부터 BFS 탐색을 사용해 각 섬에서부터의 거리를 채워나간다. 그러다 동시에 두 섬에 의해 영향을 받는 타일을 체크하여 그 거리를 구한다

```c
while(!q.empty()){
	int first = q.front().first;
	int second = q.front().second;
	q.pop();
	for(int k=0;k<4;k++)    //방향 배열 사용
	{
		int x,y;
		x = first+dx[k];
		y = second+dy[k];
		if( (x>=0 && x<n) && (y>=0 && y<n) )
		{
			if(arr[y][x] == 0) {
				if (group[y][x] == 0)
				{
				group[y][x] = group[second][first];
				weight[y][x] = weight[second][first]+1;
				q.push(make_pair(x,y));
				}
			else if(group[y][x] != group[second][first])
			{
				int tmp = weight[y][x] + weight[second][first];
				if( tmp < minValue )
					minValue = tmp;
			}
			}
		}
	}
}   
```

### 배운 점

- 각 그룹을 나누고 각각의 그룹으로부터 채워나가는 요령
- 이 방법이 아니면 각 그룹으로 나눈 후 각 섬까지 얼마나 걸리는지 여러번 bfs  를 돌려서 확인하는 방법도 있다. 하지만 위의 방법이 효율적
