---
layout: post
title: BaekJoon-no.1799 비숍
categories:
- Algorithms
tags: algorithms programming dfs backtracking
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/1799)

체감 난이도(1~5) : 4.0

### 풀이

어려워던 문제. 
모든 필드가 1로 채워져있고 맵의 크기가 최대인 10x10 이 나와서 2^(10x10)의 시간복잡도가 나와버린다. 나는 시간복잡도가 크지만 백트래킹을 통해서 유망하지 않은 분기점들을 들어가지 않으니 처리될거라고 생각했으나 그리 만만한 문제가 아니었다.  결국 다른사람들의 풀이를 참고해서 풀었는데, 핵심은 게임판을 2개로 나누는 것이다.

```
0*0*0
*0*0*
0*0*0
*0*0*
0*0*0

과

*0*0*
0*0*0
*0*0*
0*0*0
*0*0*

로 대각선에 따라서 두 개의 게임판으로 나눈다.
```

비숍의 특성상 대각선만 신경을 써주면 되기 때문에 두 개의 판으로 나눌 수 있기때문.  이렇게 두 개의 판으로 나눈 뒤 각각을 DFS + 백트래킹으로 계산하면 2^(5x5) 가 두번 나오므로 충분히 제한시간 내에 풀 수 있다.


```c++
void makegroup(int row, int depth,int ver)
{
	if (depth >= n)
	{
		if (row == n-1)
		{
			calc(ver);
			return;
		}

		row++;

		if (ver == 0)
		{
			if (row % 2 == 0)
				depth = 0;
			else
				depth = 1;
		}
		else
		{
			if (row % 2 == 0)
				depth = 1;
			else
				depth = 0;
		}

		makegroup(row, depth, ver);// 다음 줄 호출
		return;
	}

	if (arr[row][depth] == 1)		// 비숍 놓을수 있는 자리.
	{
		if (check(row, depth))
		{
			visited[row][depth] = true;			// 비숍 놓고 dfs 
			makegroup(row, depth + 2, ver);
			visited[row][depth] = false;
		}

	}

	makegroup(row, depth + 2, ver);		// 비숍 안놓고 dfs

	return;
}
```


### 배운 점

- 백트래킹으로만 시간복잡도가 줄을 거라는 안일한 생각으로 푼 걸 반성함
- 문제의 특성`비숍의 특징` 을 이용해 게임판을 나누고 그로 인해 시간복잡도를 나누는 법을 배움
- dfs를 1차원? 이나 일렬로 정렬되어있는 것만 해봤는데, 이 문제는 2차원? 스럽게 dfs를 할 수 있었다.
