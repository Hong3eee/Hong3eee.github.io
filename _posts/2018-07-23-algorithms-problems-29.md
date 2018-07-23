---
layout: post
title: AlgoSpot-Problem. 두니발 박사의 탈옥
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://algospot.com/judge/problem/read/NUMB3RS)

체감 난이도(1~5) : 3.0

### 풀이

2차원 배열으로 dp를 이용해 문제를 푼다.  `d[days][where]` 형태로 배열을 세운 후 day-1의 배열을 이용해 현재 day를 채워넣는다.

```c++
for(int i=0;i<d;i++)
	for(int j=0;j<n;j++)
	{
	if(ans[i][j] > 0.0) // 이 전에 있을 확률
		for(int k = 0; k<n;k++)
			if(a[j][k] == 1)    //연결되어있음
				ans[i+1][k] += ans[i][j] / connected[j]; //connected 배열은 j 마을에 연결된 다른 마을의 수를 저장하고있음
	}
```

### 배운 점

- `connected[]` 배열을 이용해 귀찮은 계산을 초기에 입력받을 때 한번만 해준다. 구현이 매우 쉬워짐.

