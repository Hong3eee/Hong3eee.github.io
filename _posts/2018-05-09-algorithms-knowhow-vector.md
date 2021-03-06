---
layout: post
title: STL vector 사용법
categories:
- Algorithms
tags: algorithms data-structure STL
comments: true
---

벡터 Vector

### 정의

- 자동으로 메모리가 할당되는 배열. 동적 메모리 관리에 편리
- 원소가 하나의 메모리 블록에 연속하게 저장된다

### 사용법

```c++
#include <vector>

int main(){

	vector<Type> v;
//	vector<Type> v(10);
//	vector<int> v(10,2);

	v.push_back(1);
	v.push_back(3);
	v.push_back(2);

	v[0]; // 1
	v.front(); // 1
	v.back(); // 2
	v.size(); // 3

	return 0;
}
```

- vector<Type> v : type 형을 가지는 비어있는 vector 생성
- vector<Type> v(10) : type 형을 가지며 초기값으로 초기화된 vector 생성
- vector<int> v(10,2) : int 형을 가지며 2로 초기화된 원소 10개를 가지는 vector 생성
- v[index] : index 번째 원소 참조
- v.front() : 첫 번째 원소 참조
- v.back() : 마지막 원소 참조
- v.push_back(x) : 마지막에 x 삽입
- v.pop_back() : 마지막 원소 제거
- v.begin() : 첫 번째 원소 가르킴
- v.end() : 마지막 원소 그 다음을 가르킴
- v.size() : 원소의 갯수 리턴
- v.empty() : 벡터가 비어있으면 true 리턴
- v.erase(v.begin() + 1) : index = 1번째 원소 삭제
- v.erase(v.begin() + 1, v.begin() + 3) : index = 1 ~ 3 번째까지 원소 삭제

- ++ vector<int> a(10) 과 vector<int> a[10]은 매우 다르다! 전자는 크기가 10짜리인 vector를 하나 선언(=int a[10]) 인 반면 후자는 vector 원소를 10개 가지는 하나의 배열을 선언한 것이다 (=vector < vector < int > > a(10))
