---
layout: post
title: BaekJoon-no.12865 평범한 배낭
categories:
- Algorithms
tags: algorithms programming dp knapsack
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/12865)

체감 난이도(1~5) : 3.0

### 풀이

전형적인 냅색 문제. 메모이제이션 보다는 항상 풀던 bottom up 방식으로 해결함.  가방에 어떤 물건들이 담겨져 있는지 확인하려면 d 배열의 값이 다른 경우를 출력해준다.


```c
for(int i =1;i<=n;i++)
	for(int j =1;j<=k;j++)
	{
		if(j - w[i] < 0)    //무게를 넘어간다면(선택하지 않을때와 같음)
			d[i][j] = d[i-1][j];
		else
		{
			int select = d[i-1][j-w[i]] + v[i] ; 
			// i 번째 아이템은 무조건 고를거야, 그 후 남는 공간 최대로 쓰는>방법 더해줘, DP! 부분문제의 활용
			int notselect = d[i-1][j];

			d[i][j] = select > notselect ? select : notselect; //부분문제의 해결
		}
	}
```

### 배운 점

- knapsack 문제 해결법, 기본적인 코딩방법을 배움.
- 다시봤을때 헷갈리면 주석이 큰 역할을 할 것만 같은 느낌적인 느낌이다.
- 배열로 knapsack 을 풀면 배열의 가장 끝이 최대값이다!
