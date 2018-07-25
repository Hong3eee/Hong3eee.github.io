---
layout: post
title: AlgoSpot-Problem. 여행 짐 싸기
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://algospot.com/judge/problem/read/PACKING)

체감 난이도(1~5) : 3.5

### 풀이

knapsack 문제 + knapsack 에 들어가는 내용물 까지 출력하는 문제.  
냅색의 경우 기존 냅색문제 풀이 방식대로 똑같이 풀면 된다. 그리고 내용물은 만들어진 배열을 이용해서 답을 도출한다. 2차원 배열의 맨 마지막부터 접근하여 아이템의 갯수 i에 따라서 i 와 i-1 번째 의 배열 d 값이 다르다면 i 번째 아이템을 가방에 담은 것으로 판단한다.

```c++
for(int i =1;i<=n;i++)          //전형적인 냅색 문제
	for(int j =1;j<=w;j++)
	{
		if( j - weight[i] < 0)
			d[i][j] = d[i-1][j];
		else
		{
			int select = d[i-1][j-weight[i]] + value[i];
			int notselect = d[i-1][j];
			d[i][j] = max(select,notselect);
		}
	}

int cnt = 0;
stack<int> item;
int we= w;

for(int i = n; i>0;i--)     // 가방에 들어가는 내용물 도출
{
	if(d[i][we] != d[i-1][we])
	{
		cnt++;
		item.push(i);
		we -= weight[i];
	}
}
```

### 배운 점

- `d[i-1][w]` 와 `d[i][w]` 의 값이 다르다면 i 번째 아이템을 가방에 갖고 있다. 처럼 d 배열을 이용해서 최적해의 구성요소를 찾을 수 있는 경우도 있다.

