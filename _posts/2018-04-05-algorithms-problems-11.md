---
layout: post
title: BaekJoon-no.11054
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/11054)

체감 난이도(1~5) : 2.5

### 풀이

앞에서 부터 증가하는 수열을 담은 d[],  
뒤에서 부터 증가하는 수열을 담은 d2[] 를 구한다.  
그 후 두 배열을 더한 값이 최댓값을 출력해준다.  

d[] , d2[] 를 구할 땐, n번째 값이 들어갔을 때 가장 긴 수열을 d[j](0<j<n) 을 이용해서 구한다.  

```c
for(int i = 1; i<N+1;i++)
{   
	d[i] = 1;
	for(int j = 1; j<i;j++)
	{
		if(a[i] > a[j] && d[i] < d[j] + 1)
		d[i] = d[j] + 1;
	}
}   
for(int i = N; i>0;i--)
{   
	d2[i] = 1;
	for(int j = N; j>i;j--)
	{
		if(a[i] > a[j] && d2[i] < d2[j] + 1)
		d2[i] = d2[j] + 1;
	}
}   

int tmpmax =0; 
for(int i = 1; i<N+1;i++)
	tmpmax = max(tmpmax,d[i]+d2[i]);
printf("%d\n",tmpmax-1);
```

### 배운 점

- -
