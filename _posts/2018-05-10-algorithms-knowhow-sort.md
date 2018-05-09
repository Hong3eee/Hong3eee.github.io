---
layout: post
title: STL sort 사용법
categories:
- Algorithms
tags: algorithms data-structure STL sort
comments: true
---

정렬 Sort

### 정의

- 어떠한 데이터들을 순서대로 배치시키는 것을 의미
- <algorithm> 헤더 파일에 속해있음. [start,end) 범위의 인자를 정렬함
- STL sort() -> O(nlgn) 의 quick sort를 내부 함수로 구현, stable_sort() -> O(nlgn) 의 merge sort를 내부 함수로 구현했다.
- 오름차순 정렬이 기본값

### 사용법

- sort(arr,arr+n)

- sort(v.begin(),v.end())

- sort(v.begin(),v.end(),greater<type>()) // 내림차순

- sort(v.begin(),v.end(),cmp)  // 사용자 정의 함수
```c++
bool cmp(const pair<int,int> &u, const pair<int,int> &v){
	return (u.first>v.first);
}

...

sort(v.begin(),v.end(),cmp) // cmp 함수에 맞게 정렬함
```

- ++ pair를 sort함수로 정렬할 경우, pair의 첫번째 원소를 기준으로 정렬한다

- +++ 정렬할 데이터 중 같은 비교 대상이 있을 때, 그 순서를 유지하며 sort 하는 함수 -> stable_sort(start,end) 를 사용한
다
