---
layout: post
title: STL stack 사용법
categories:
- algorithms
tags: algorithms data-structure STL
commnets: true
---

스택 Stack

### 정의

- 한쪽에서만 자료를 넣고 뺄 수 있는 자료구조
- LIFO(Last In First Out)

배열로 큰 어려움 없이 구현할 수 있으나,  
실제 알고리즘 대회나 코딩테스트 환경에선 시간이 촉박하므로  
만들어진 자료구조를 쓰는것이 유용하다.

### 사용법

```c++
#include <stack>

int main(){

	stack<Type> var;

	stack.push(~~);
	stack.pop();
	stack.size();
	stack.empty();
	stack.top();

	return 0;
}
```

- push() : data를 스택에 삽입, 스택의 size는 +1 이 된다
- pop() : 스택의 가장 위에 있는 data를 가져오면서 스택에서 삭제, size는 -1
- top() : 스택의 가장 위에 있는 data를 가지오지만 스택에서 삭제는 안함
- empty() : 스택이 비어있는지, 아닌지 확인. 비어있을시 true 반환
- size() : 스택의 현재 사이즈를 반환










