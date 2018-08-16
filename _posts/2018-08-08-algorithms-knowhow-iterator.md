---
layout: post
title: STL Iterator 사용법
categories:
- Algorithms
tags: algorithms stl iterator
comments: true
---

Iterator 반복자

### 정의

- 컨테이너들의 원소를 순회할 수 있도록 하는 접근 객체
- 이 Iterator를 통해 각자의 내부 구조들이 다른 컨테이너들을 관리할 수 있다 
- 즉, 순회하는 방법의 일반화

### 사용법

```c++
#include <iostream>
#include <cstdio>
#include <vector>

using namespace std;

int main(){

	vector<int> v;
	v.push_back(1);
	v.push_back(2);
	v.push_back(3);
	v.push_back(5);
	v.push_back(4);

	vector<int>::iterator it;

	it =v.begin();
	cout << it[3];<< endl; // []연산을 통해 임의 접근	

	for (it=v.begin();it!=v.end();++it) { // it 를 증가시킬 때, 전위연산자로 하는게 효율이 좋다. 후위 연산자는 메모리 상에 값을 복사한 후, 증가시켜서 바꾸는 방식이라고 한다.
		printf("%d\n",*it);
	}
	/*
	   for(vector<Student_info>::const_iterator iter = students.begin(); 
	   iter != students.end(); ++iter) 	// 구조체, 멤버 접근
	   {     
	   cout<< (*iter).name <<endl; 
	   cout<< iter->name <<endl; 
	   }
	 */
	return 0;
}
```

- 연산자들을 지원한다. 포인터와 매우 유사
- `*iter` : 현재 가르키고 있는 원소 값
- `iter->x` : `(*iter).x` 와 동일, 객체의 멤버에 접근
- `iter ++ / --` : 다음 / 이전 원소
- `iter != / ==` : 같은 위치를 가르키는 지 판별
- `iter =` : 반복자를 할당

