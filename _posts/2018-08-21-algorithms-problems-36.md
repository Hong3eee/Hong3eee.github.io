---
layout: post
title: BaekJoon-no.3055 탈출
categories:
- Algorithms
tags: algorithms programming bfs
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/3055)

체감 난이도(1~5) : 2.5

### 풀이

  BFS 문제. 초급과 중급 그 사이에 있는 난이도로 여겨진다. 기초적인 bfs와 다르게 2개의 큐를 써서 풀어야 했고 이게 좀 신선했다. 생각보다 헤맨문제이다. 처음엔 물이 차오르는 배열, 고슴도치가 움직이는 배열 두개로 풀어서 목적지에 고슴도치가 먼저 들어오면 그 거리를 출력하게끔 구현했다. 테스트케이스는 다 통과하길래 문제없이 되는 줄 알았는데 그게 아니었다. 입력이 커지면 중간에 겹칠 위험이 있기 때문에 이렇게 풀면 안됐다.  심기일전해서 다시 풀었는데. 이번엔 물이 퍼져나가는 bfs 한번 수행, 고슴도치의 이동 bfs 한번 수행 하는식으로 풀었다. 문제에서 나온 것과 같이 `고슴도치는 물이 찰 예쩡인 칸으로 이동할 수 없다.` 라는 조건을 해석해 물 bfs 를 먼저 수행해줘야 한다.

```c++

void water_bfs(){
	int wqsize = wq.size();
	while(wqsize-- > 0){
		int y = wq.front().first;
		int x = wq.front().second;

		wq.pop();
		for(int i=0;i<4;i++)
		{
			int nexty = y + dy[i];
			int nextx = x + dx[i];

			if(0<= nexty && nexty <r && 0 <= nextx && nextx < c)
				if(arr[nexty][nextx] == '.' && check[nexty][nextx] == 0)
				{
					arr[nexty][nextx] = '*';
					wq.push(make_pair(nexty,nextx));
					check[nexty][nextx] = -1;
				}
		}
	}
	return ;
}
void bfs(){
	while(!sq.empty()){

		water_bfs(); //물 먼저

		int sqsize = sq.size();	// 고슴도치 큐 사이즈를 이용해 현재 칸에서 한번씩만 둘러볼 수 있게 한다.
		while(sqsize-- > 0){
			int y = sq.front().first;
			int x = sq.front().second;

			sq.pop();

			for(int i=0;i<4;i++)
			{
				int nexty = y + dy[i];
				int nextx = x + dx[i];

				if(0<= nexty && nexty <r && 0 <= nextx && nextx < c)
					if(arr[nexty][nextx] == '.' && check[nexty][nextx] == 0)
					{
						sq.push(make_pair(nexty,nextx));
						check[nexty][nextx] = check[y][x] + 1;
					}
					else if(arr[nexty][nextx] == 'D' && check[nexty][nextx] ==0)
						check[nexty][nextx] = check[y][x] + 1;
			}
		}
	}
}

```


### 배운 점

- 큐 두개 쓰는건 처음 해봤다. 익숙해지자
- `check[][]==0` 조건을 안써서 한시간 헤맸다. 실전에서 이런 실수 없도록 차근차근 코딩하는 습관을 들이자. 너무 빨리만 풀려고 했었다.
