---
layout: post
title: BaekJoon-no.11652 카드
categories:
- Algorithms
tags: algorithms programming sorting
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/11652)

체감 난이도(1~5) : 1.5

### 풀이

주어진 입력을 한 번 정렬한 후 풀면 O(N) 만에 풀 수 있다.  정렬된 = 연속된 같은 수의 숫자를 세고 이를 이용해 풀어준다.



```c
for(int i = 0 ; i<n;i++)
{   
	scanf("%lld",&x);
	v.push_back(x);
}   
sort(v.begin(),v.end());
long long int ans=v[0];
int cnt_max=1,cnt=1;

for(int i = 1 ; i<n;i++)
{   
	if(v[i] == v[i-1])
		cnt++;
	else
		cnt = 1;

	if(cnt_max < cnt)
	{
		cnt_max = cnt;
		ans = v[i];
	}
}   
```

### 배운 점

- vector 사용법에 대해 조금 알게 됨. vector 포스팅을 따로 할 예정
- sort 함수 사용법 숙지함
- 처음에 vector<pair<int,int>> 이런 자료구조로 풀려고해서 너무 어렵게 접근함. 그냥 정렬 한 번만 해주면 쉽게 풀리는 문제. 문제를 쉽게 풀려고 노력하자!

