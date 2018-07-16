---
layout: post
title: AlgoSpot-Problem. Pi
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://algospot.com/judge/problem/read/PI)

체감 난이도(1~5) : 2.5

### 풀이

3,4,5 개 씩 끉어서 외운다는 조건을 이용해 구현한다. 풀이 1의 경우, 3,4,5 개 마다 완전탐색을 시도하고, 풀이 2의 경우, 3,4,5 개 전의 배열 값을 이용해 채워나간다.

```c++
//풀이 1. 메모이제이션을 이용한 top down 방식
int memo(int start)
{
	if(start == s.size()) return 0;
	int& ret = d[start];
	if(ret != -1) return ret;

	ret = 10000000;
	for(int i = 3 ; i<=5;i++)
		if(start + i <= s.size())
			ret = min(ret , memo(start + i ) + check( start , start + i - 1));

	return ret;
}
	
cout << memo(0) << endl;

// ---------------------------------
// 풀이 2. 배열, 작은 부분문제를 이용해 다음 배열을 채워가는 방식의 bottom up
d2[2] = check(0,2);
d2[3] = check(0,3);
d2[4] = check(0,4);
for(int end=5; end < s.size(); end++)
{
	int tmp = 1000000;
	for(int j = 3;j<=5;j++)
	{
		if(d2[end-j] != -1)
			tmp = min(tmp,d2[end-j]+ check(end-j+1,end));
	}
	d2[end] = tmp;
}
cout << d2[s.size()-1] << endl;
```

### 배운 점

- -

