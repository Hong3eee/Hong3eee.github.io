---
layout: post
title: BaekJoon-no.10844
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/10844)

체감 난이도(1~5) : 2.5

### 풀이

DP에서 풀이에 사용하는 배열을 2차원으로 선언해서 푼다.  
d[N][i]는 N자리의 계단수 중 i 숫자로 끝나는 계단수의 갯수를 나타내도록 배열을 선언하자.   
이 배열을 이용해 풀이하자.

```c
for(int i = 2;i<N+1;i++)
	for(int j = 0;j<10;j++)
	{
		if(j==0)
			d[i][j] = d[i-1][j+1];
		else if(j==9)
			d[i][j] = d[i-1][j-1];
		else
			d[i][j] = d[i-1][j-1] + d[i-1][j+1];
		d[i][j] %= mod;
	}

```

### 배운 점

- 큰 수가 나왔을 때, long long 형으로 표현하는것이 신변에 좋다
- 이 문제 또한 N번째에 들어올 경우의 수를 생각해서 점화식을 세우면 풀 수 있다. 그런데 2차원 배열이라는 점에서 N번째에 들어올 경우의 수를 좀 더 세분화 했다는 것을 기억해두자.
- 백준 문제만의 특징인진 모르겠는데, 최종 결과값에 나머지 연산을 하는게 아니라 중간중간 값에 나머지 연산을해서 더해준다. 왜 이러는건지 확실힌 모르겠지만 유념해두자.
