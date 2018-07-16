---
layout: post
title: C++ String 사용법
categories:
- Algorithms
tags: algorithms string container
comments: true
---

String container

### 정의

- char[] 의 컨테이너, 문자열을 다루기 쉽도록 만든 컨테이너

### 사용법

```c++
#include <string>

int main(){

	string str= "abcd";
	string str2("zxc");
	string str3(str2);		//생성 방법들

	str[i];
	str.at(i);		// 원소 접근

	str.empty();	// 비어있으면 true, 아니면 false

	str.size();		// 길이

	str.find("b");	// 문자열이 발견된 첫 위치 리턴

	string str4;
	str4=str;		// 문자열 복사

	str.append("~~~");
	str+str2; 		// 문자열끼리 이어붙이는 연산 지원

	str.insert(2,"zxcv");	// 인덱스 2 위치에 zxcv 문자열 삽입

	str.replace(2,11,"zxcv");	// 인덱스 2위치부터 11개 문자를 zxcv로 대체

	str.substr(0,2);	// 부분 문자열, 첫번째 인자부터 두번째 인자 수 만큼 문자열 리턴
	str.substr(0);		// 0번째 인자부터 끝가지 부분 문자열로 리턴

	cin >> str;
	cout << str;	// 입출력, string은 cin 으로만 입력가능

	str.compare(str2);	// 비교, 문자열이 같다면 0, str이 str2보다 앞선다면 음수값, 반대라면 양수값 리턴

	str.erase(2,3);	// index = 2 부터 원소 3개 삭제



	string() + "~~~~" // 이 방법으로 문자열 생성 가능, tip!

	return 0;
}
```
