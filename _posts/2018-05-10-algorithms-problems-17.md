---
layout: post
title: BaekJoon-no.11004 K번째 수
categories:
- Algorithms
tags: algorithms programming sorting
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/11004)

체감 난이도(1~5) : 1.0

### 풀이

주어진 수 정렬 후 출력


```c
//  vector<int> v;
int v[N];

int N,K;
scanf("%d",&N);
scanf("%d",&K);

int x;
for(int i =0;i<N;i++)
{   
	scanf("%d",&v[i]);
//      scanf("%d",&x);
//      v.push_back(x);
}   

//  sort(v.begin(),v.end());
sort(&v[0],&v[N]);

printf("%d\n",v[K-1]);

```

### 배운 점

- vector를 이용해 쉽게 정렬하려고 했으나 시간초과 에러 뜸. 배열을 이용해 다시 정렬하니 통과됨. 즉, 벡터보단 배열이 빠르다!
- sort 함수를 쓸 때 벡터는 sort(v.begin(),v.end()) 로 사용함.
- 배열을 이용해 sort할땐 sort(&v[0],&v[N]) 으로 맨 처음 주소 ~ 마지막 원소 그 다음번지 주소를 인자로하여 사용함!!

