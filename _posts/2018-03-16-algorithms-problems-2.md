---
layout: post
title: BaekJoon-no.9012
categories:
- Algorithms
tags: algorithms programming stack
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/9012)

체감 난이도(1~5) : 1

### 풀이

여러 풀이방법이 있겠지만 스택으로 푸는것이 가장 쉬워보인다.


```c
for(int k =0; k<j ; k++){
	if(input[k]==')'){
		if(stack.empty()){
			cnt = -1; 
			break;
		}
		else
			stack.pop();
	}
	else
		stack.push(input[k]);
}
```

### 배운 점

- 스택 기본 사용법에 대한 숙지
- STL로 구현되어 있는건 갖다쓰자! 실전에선 시간이 부족하다
