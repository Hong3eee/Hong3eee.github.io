---
layout: post
title: BaekJoon-no.10799
categories:
- etc
tags: algorithms programming
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/10799)

체감 난이도(1~5) : 1.5

### 풀이

스택을 이용해 푼다.  
'(' 괄호가 나왔을 때 스택에 push, ')' 가 연속으로 나왔을 땐 결과값에 스택 사이즈만큼 더해주고 ')' 나오되 연속하지 않았을 땐 쇠막대기 조각이 1개만 나오므로 1만 더해줌.


```c
for(int i =0; i<len ; i++){
	if(input[i]=='('){
		stack.push(i);
	}
	else
	{
		tmp = stack.top();
		stack.pop();
		if( tmp == i-1)
			sum += stack.size();
		else
			sum += 1;
	}
} 
```

### 배운 점

- 스택 기본 사용법에 대한 숙지
