---
layout: post
title: AlgoSpot-Problem. 회전초밥
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://algospot.com/judge/problem/read/SUSHI)

체감 난이도(1~5) : 2.5

### 풀이

평범한 dp 문제. 풀이는 쉬우나 공간복잡도를 고려해줘야한다.  
슬라이딩 윈도우 기법을 이용해 풀면 매우 효율적인 공간복잡도를 얻을 수 있다.

```c++
// 원래 풀이. 그냥 풀어도 통과 되긴했음.
memset(d,0,sizeof(d));
int ret = 0;
for(int i = 1 ; i <= m ; i++)
{
	for(int j =0 ; j < n; j++)
	{
		if(i >= price[j]) 
		{   
			int tmp = d[i - price[j]];
			d[i] = max(d[i] , tmp + value[j]);
		} 
	}
	ret = d[i];
}

// 책에 있는 코드. 보고 배우자
int sushi3() {
	int ret = 0;
	c[0] = 0;
	for(int budget = 1; budget <= m; ++budget) {
		int cand = 0;
		for(int dish = 0; dish < n; ++dish)
			if(budget >= price[dish])
				cand = max(cand, c[(budget - price[dish]) % 201] + pref[dish]);	// % 연산을 이용해 이전에 사용했던 공간을 고대로 사용한다. 슬라이딩 윈도우 기법
			c[budget % 201] = cand;
	
		ret = max(ret, cand);
	}
	return ret;
}

```

### 배운 점

- 슬라이딩 윈도우 기법. 공간복잡도를 줄이는 효율적인 기법. 메모이제이션과 재귀를 이용한 dp에서는 쓰기 힘들지만 내가 주로 푸는 방법인 반복적 dp(bottom up) 방식에서 사용할 수 있다. 
- 예제 ) `d[n%2][x] =max( d[(n+1)%2][x] , d[(n+1)%2][x+1] ) + arr[n][x]` 
- 문제에서 100 단위로 가격이 주어진다는 것을 생각해서 공간복잡도를 1/100 으로 줄였다. 문제를 잘 읽자.
