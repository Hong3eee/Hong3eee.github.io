---
layout: post
title: STL pair 사용법
categories:
- Algorithms
tags: algorithms data-structure STL pair
comments: true
---

페어 Pair

### 정의

- 두 데이터를 하나의 페어 객체로 묶어주는 클래스
- <algorithm>,<utility> 헤더 파일에 속해있음. 
- 어떤 데이터들의 쌍을 표현할때 많이사용. x,y좌표 등
- vector와 주로 사용함

### 사용법

```c++
pair <int,int> p = make_pair(1,2);
p.first // 1
p.second // 2

vector<pair<int,string>> v;
v.push_back(make_pair(1,"kim"));
v.push_back(make_pair(3,"lee"));
v.push_back(make_pair(2,"park"));

v[0] // 1,"kim"
v[1] // 3,"lee"
v[2] // 2,"park"

sort(v.begin(),v.end());

v[0] // 1,"kim"
v[1] // 2,"park"
v[2] // 3,"lee"
```
- pair<type1,type2> p

타입 1, 2를 데이터로 가지는 페어 p 생성

- p.first, p.second

p의 첫번째, 두번째 인자

- make_pair(x,y)

x,y의 쌍의 값을 가지는 pair 생성

- sort 함수에 의해서 정렬 가능. 기본적으로 첫번째 인자로 비교, 같으면 두번째인자로 비교
