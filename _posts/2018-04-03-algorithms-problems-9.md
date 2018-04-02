---
layout: post
title: BaekJoon-no.9465
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/9465)

체감 난이도(1~5) : 3

### 풀이

전형적인 DP문제와 같이 N 번째에 어떻게 올 수 있는지를 고려한다.  
N번째 열에 있는 스티커를 0 - 안뗌, 1 - 1행의 것을 뗌, 2 - 2행의 것을 뗌. 으로 나누어서 푼다.  

```c
for(int j=2;j<n+1;j++)
	for(int k=0;k<3;k++)
	{
		tmpmax = 0;
		for(int l=0;l<3;l++)
		{
			if( l == k)
				continue;
			tmpmax = max(tmpmax,d[j-1][l]);
		}
		d[j][k] = tmpmax + p[j][k];
	}
```

### 배운 점

- 역시 DP 문제는 N 번째에 뭐가 들어올지 경우를 나누어서 풀면 쉽게 풀 수 있다
