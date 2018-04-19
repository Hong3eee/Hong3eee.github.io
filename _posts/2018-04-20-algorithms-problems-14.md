---
layout: post
title: BaekJoon-no.1699 제곱수의 합
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/1699)

체감 난이도(1~5) : 2.5

### 풀이

n보다 작은 수 중에 제곱수 ( 1x1, 2x2, 3x3, ... ) 를 하나씩 n을 구성하는 항으로 생각해서 푼다.

```c
for(int i =1;i<N+1;i++)
{   
	int tmp = 100001;
	for(int j=1;j*j<=i;j++)
	{
		tmp = min(d[i-j*j]+1,tmp);
		d[i] = tmp;
	}
}   
```

### 배운 점

- 처음에 생각한 로직이 맞았는데 sqrt등의 함수를 쓰려고 해서 좀 헤맸다.
- sqrt -> i x i 등으로 바꿀 수 있음을 생각하자.
- 쉽게 풀려고 노력하자
