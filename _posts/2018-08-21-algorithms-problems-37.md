---
layout: post
title: BaekJoon-no.2206 벽 부수고 이동하기
categories:
- Algorithms
tags: algorithms programming bfs
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/2206)

체감 난이도(1~5) : 3.0

### 풀이

check 배열을 3차원으로 사용하는걸 생각 못해서 꽤 시간을 많이썼다. 결국엔 다른 사람의 코드를 참고해서 풂.  
벽을 만나면 상태변수를 + 1 하고 check 배열에도 +1 차원에 저장시키면서 진행한다. 벽을 만난 노드와, 안만난 노드 둘 다 하나의 큐로 푸쉬 시켜서 서로 한 단계씩 진행한다.


```c++
int arr[1000][1000];
int check[2][1000][1000]; //상태 2개 저장

int dy[4] = {1,0,-1,0};
int dx[4] = {0,1,0,-1};

struct info{
	int y,x,s;
};

int m,n;
void bfs(int y,int x,int status){ //status = 0 벽아직 안뚫, = 1 뚫
	queue<info> q;
	info in;
	in.y = y;
	in.x = x;
	in.s = status;

	q.push(in);

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
				if(arr[nexty][nextx] == 1 && s == 0)//벽을 부수지 않은 상태에서 벽을 만나면 부순다.
					//다른 부수지 않는 노드에 의해서 다시 부서져도 최단경로를 찾기 때문에 에러 X
				{
					check[1][nexty][nextx] = check[0][y][x] + 1;

					info next;
					next.y = nexty;
					next.x = nextx;
					next.s = s + 1;

					q.push(next);

				}
				else if(arr[nexty][nextx] == 0 && check[s][nexty][nextx] == 0)
				{
					//벽이 아니라면 상태를 유지하며 계속 진행
					info next;
					next.y = nexty;
					next.x = nextx;
					next.s = s;

					q.push(next);

					check[s][nexty][nextx] = check[s][y][x] + 1;

				}
			}
		}
	}
	return ;
}
```


### 배운 점

- 큐 하나로 두 개의 상태를 다루는 방법!
- 상태변수? 로 3차원을 선택한다. 꼭 맵이 2차원이라고 해서 2차원 check배열로 풀려고만 생각하지말자. 
