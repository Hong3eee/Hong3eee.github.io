---
layout: post
title: BaekJoon-no.9328 열쇠
categories:
- Algorithms
tags: algorithms programming bfs
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/9328)

체감 난이도(1~5) : 3.5

### 풀이

꽤 어려워던 문제.  풀었던 BFS탐색 문제 중에 가장어렵지 않나 싶다. BFS 문제를 처음 풀기 시작했을때 이 문제를 보다가 포기하고, 한 1주일 공부하고 나서 푸니 풀만했다. 핵심은 탐색을 하다가 문을 만나면 일단 문을 큐,벡터 등의 자료구조로 저장, 키를 만나면 가진 키로 문을 열어준 후 BFS 탐색을 다시 시작하면 된다.
				   이렇게 풀고 나니깐 쉬워보이는데 지금껏 풀었던 전형적인 BFS 문제와 달라서 어려웠다.
```c++
void door_check()
{
	int len = doorq.size();
	while(len--)
	{
		info front = doorq.front();
		int y = front.y;
		int x = front.x;

		char c = arr[y][x];

		if(keys[c - 'A'] == 1)	//키가 있다면 큐에서 제거, bfs탐색 큐에 좌표를 넣어준다.
		{
			arr[y][x] = '.';
			check[y][x] = 1;

			q.push(info(y,x));
			doorq.pop();
		}
		else	// 키로 문을 열 수 없다면 큐의 맨 뒤로 보내서 다음 노드를 처리할 수 있게 한다.
		{
			doorq.pop();	
			doorq.push(front);
		}
	}
	return;
}
void bfs()
{
	door_check();

	while(!q.empty())
	{	
		int y = q.front().y;
		int x = q.front().x;

		q.pop();

		for(int i = 0; i<4;i++)
		{
			int ny = y + dy[i];
			int nx = x + dx[i];

			if( 0 <= ny && ny < h && 0 <= nx && nx < w)
			{
				if(arr[ny][nx] == '.' && check[ny][nx] == 0)
				{
					check[ny][nx] = 1;
					q.push(info(ny,nx));
				}
				else if(arr[ny][nx] == '$')
				{
					ans++;
					arr[ny][nx] = '.';
					check[ny][nx] = 1;
					q.push(info(ny,nx));
				}
				else if(arr[ny][nx] != '*')
				{
					if('A' <=arr[ny][nx] && arr[ny][nx] <= 'Z')
					{
						doorq.push(info(ny,nx));
						door_check();
					}
					if('a' <=arr[ny][nx] && arr[ny][nx] <= 'z')
					{
						keys[arr[ny][nx] - 'a'] = 1;
						arr[ny][nx] = '.';
						check[ny][nx] = 1;
						q.push(info(ny,nx));
						door_check();
					}
				}

			}
		}
	}
	return ;
}
```


### 배운 점

- 코드가 매우 더럽다. 아무래도 키,문서,문 등을 만났을때 처리해줘야하는 부분들이 많아서 그런듯하다. 풀고 나서 다른 사람들의 코드를 보는데, 꽤 유용한 스킬을 발견했다.

```
.......
.?????.
.?????.
.?????.
.?????.
.?????.
.......
```

- 이 문제에서는 어느곳이 시작점인지 알 수 없다는 조건이 있다. 그래서 이를 해결하기 위해, 위와 같은 스킬을 사용할 수 있다. `?`로 표시한 부분이 실제로 들어오는 지도 입력이고, `.` 은 개발자가 추가한 부분이다. 이렇게 맵을 구성하면 bfs를 호출할 때, bfs(0,0)만 호출해서 간단히 처리할 수 있다. 이런 스킬 배워두자.

- 아 그리고 문제가 또 까다로웠던 게 키를 어떻게 저장할 것인가? 이다.
- 이 또한 키의 입력이 알파벳인걸 보고 keys[0~26] 배열에 `입력받은 캐릭터 값 - 'a'`를 인덱스로 사용해서 처리해줬다. 그럼 `a -> index = 0, b -> index = 1 ...` 으로 표현 가능하다. 깔끔!
