---
layout: post
title: STL Map 사용법
categories:
- Algorithms
tags: algorithms stl container map
comments: true
---

Map 맵

### 정의

- Map 은 key 와 value 로 구성되어 있으며 key 값으로 정렬이 된다. b tree의 변형인 레드블랙트리로 내부적인 구성이 되어있다
- key 값은 중복을 허용하지 않는다
- `<map>` 헤더파일을 추가해줘야 한다

### 사용법

```c++
#include <iostream>
#include <map>
using namespace std;

int main(){
	map<string,int> m;	//선언
	map<string,int,greater<string> > m2; 

	m.insert(pair<string,int>("hi",1)); 
	m["hi2"] = 2;  			// 두가지 다른 입력 방법

	cout << m["hi"] << endl;
	cout << m["hi2"] << endl;

	m["hi"] = 100; // 업데이트

	//	m.erase("hi2");
	m.erase(m.find("hi2")); //삭제 둘 다 가능

	m["hi4"] = 4;
	m["hi3"] = 3; 
	m["hi2"] = 2;
	m["hi6"] = 6; 
	m["hi5"] = 5;

	map<string,int> ::iterator iter; // 이터레이터를 통한 접근

	for(iter = m.begin() ; iter != m.end() ; iter++)
		cout << iter->first << " - key " << iter->second <<" - value " << endl;
	return 0;
}
```


- `map<type,type(,greater<type>) > m` 으로 선언 가능. 세번째 인자는 정렬 방식인데, default로 less 로 되어 있다.
- empty() : 비어 있으면 true 반환
- size() : 원소의 갯수 반환
- insert() : key,value 를 인자로 받아서 입력, `[]` 연산자를 통해서도 입력 가능
- find(key) : key 에 해당하는 이터레이터 반환
- clear() : 원소들 모두 삭제
- 정렬된 키값드을 순차적으로 접근할 땐 iterator 를 이용해서 접근한다
