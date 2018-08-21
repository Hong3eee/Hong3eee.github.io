---
layout: post
title: BaekJoon-no.14442 벽 부수고 이동하기2
categories:
- Algorithms
tags: algorithms programming bfs
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/14442)

체감 난이도(1~5) : 3.0

### 풀이

[벽 부수고 이동하기](https://hong3eee.github.io/algorithms/2018/08/21/algorithms-problems-37.html)


와 거의 비슷한 문제. K의 값만 늘어났다. 그래서 K 값만 추가해서 돌렸으나 시간초과. 왜 그런지 곰곰히 생각해보니, 다른 노드를 통해서 현재 노드가 접근하려는 곳으로 이미 들어왔을 수 있었다. 이를 bfs탐색 할 때 처리해줘야함!! 이렇게 돌리니 시간초과가 안뜸

```c++

struct info{
	int y,x,s;
	info(int _y,int _x,int _s): 
		y(_y),x(_x),s(_s) {};
};

void bfs(int y,int x,int status){ //status = s 상태에 따라 벽을 얼마나 부쉈는지
	queue<info> q;
	q.push(info(y,x,status));
	check[status][y][x] = 1;

	while(!q.empty()){
		info cur = q.front();
		q.pop();
		int y = cur.y;
		int x = cur.x;
		int s = cur.s;

		for(int i=0;i<4;i++)
		{
			int nexty = y + dy[i];
			int nextx = x + dx[i];

			if(0<= nexty && nexty <n && 0 <= nextx && nextx < m)
			{
				if(arr[nexty][nextx] == 1 && check[s][nexty][nextx] == 0 && s < k)
					// 전 노드를 통해서 이 벽을 부쉈는지 판별
				{
					check[s+1][nexty][nextx] = check[s][y][x] + 1;
					q.push(info(nexty,nextx,s+1));
				}
				else if(arr[nexty][nextx] == 0 && check[s][nexty][nextx] == 0)
				{
					q.push(info(nexty,nextx,s));
					check[s][nexty][nextx] = check[s][y][x] + 1;

				}
			}
		}
	}
}
```


### 배운 점

- 이 포스팅을 한 가장 결정적인 이유는! 바로 c++ 구조체의 초기화 방법을 익혔기 때문!!!. 코드의 가장 위쪽에 생성자를 생성하는 방법과 이 생성자를 이용해 코드를 간결화 시켰다. 실제로 이전 문제와 비교해서 코드가 꽤 짧아짐.
