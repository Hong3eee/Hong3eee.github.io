---
layout: post
title: BaekJoon-no.5015 ls
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/5015)

체감 난이도(1~5) : 4.0

### 풀이

DP 를 이용한 문제. 우선 완전탐색으로 답을 구한 후, 메모이제이션 패턴 적용을 통해 시간복잡도 효율을 높인다.  
`*` 에 해당하는 문자열이 얼마나 나올지 가늠이 안 되기때문에 하나씩 다 가봐야 한다. 즉 완전탐색으로 먼저 풀어야한다.

```c
bool match(int pi,int si){

	int& ret = d[pi][si];
	if(ret != -1) return ret;

	while( si < s.size() && pi < p.size())
	{
		if(s[si] == p[pi])
		{   
			si++;
			pi++;
		}
		else
			break;
	}

	if(pi == p.size())
		return ret = ( si == s.size());

	if(p[pi] == '*')    //recursive
	{
		for(int jump = 0 ; (si + jump) <= s.size() ; jump++)
		{   
			if(match(pi + 1,si+jump))
				return ret = 1;
		}
	}

	return ret = 0 ; 
}

```

### 배운 점

- 어려웠던 문제. 우선 완전탐색을 제대로 짜기가 힘들었다. 완전탐색 관련한 문제를 더 풀어보도록 하자.
- 이제까지 배열을 이용한 재귀를 사용하지않는 DP 문제만 풀었는데, 이 문제는 재귀를 사용하지 않고는 풀기가 어렵다. 메모이제이션 패턴으로도 풀 수 있게 연습해놓자.
- 결국 메모이제이션 패턴은 `1. 완전탐색으로 문제를 푼다. 2. 메모이제이션 패턴을 적용해 시간복잡도를 줄인다.` 이게 전부라는걸 깨달음
