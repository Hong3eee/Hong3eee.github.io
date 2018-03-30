---
layout: post
title: SW-Expert-no.1859
categories:
- Algorithms
tags: algorithms programming
comments: true
---

### 문제

[문제링크](https://www.swexpertacademy.com/main/code/problem/problemDetail.do?contestProbId=AV5LrsUaDxcDFAXc&categoryId=AV5LrsUaDxcDFAXc&categoryType=CODE&&&)

체감 난이도(1~5) : 1

### 풀이

일단 들어온 입력을 1차원 배열로 받은 후 배열의 처음부터 풀려고 했는데 생각보다 쉽지 않았다.  
고민을 하다보니 배열의 뒤에서부터 접근해서 풀면 쉽게 풀 수 있음을 깨달았다.


```c
for(int j=N;j>0;j--)
{
	if(max < arr[j-1])
		max = arr[j-1];
	else
		sum = sum + ( max - arr[j-1] );
}

```

### 배운 점

- Data에 접근할 때, 꼭 앞에서부터 하란 법은 없다.
- 생각을 뒤바꿔서 생각해보자
