---
layout: post
title: AlgoSpot-Problem. QUADTREE
categories:
- Algorithms
tags: algorithms programming divide&conquer
comments: true
---

### 문제

[문제링크](https://algospot.com/judge/problem/read/QUADTREE)

체감 난이도(1~5) : 3.0

### 풀이

Divide & Conquer 를 사용한 문제. 재귀함수를 구현하고 기저사례(탈출조건) 과 리턴값에 신경써서 코딩한다. 

```c++
string reverse(string array){
	int tmp_index = str_index;
	char c = array.at(str_index);
	str_index++;

	if(c == 'b' || c == 'w')
		return array.substr(tmp_index,1);

	string NW = reverse(array);
	string NE = reverse(array);
	string SW = reverse(array);
	string SE = reverse(array);

	return string("x") + SW + SE + NW + NE; 
}

```

### 배운 점

- string 컨테이너 사용법 숙지.
- 해당 index를 구해서 `substr(index,1)` 로 한 글자 짜리 string 생성.
- `string() + "~~~"` 로 string 생성 가능. 유용하게 쓰일 듯.

