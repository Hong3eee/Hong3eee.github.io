---
layout: post
title: STL Priority Queue 사용법
categories:
- Algorithms
tags: algorithms stl container priority_queue
comments: true
---

Priority Queue 우선순위 큐

### 정의

- Queue 의 일종으로 heap 으로 구현한 것
- `<queue>` 를 include 하여 사용한다
- `priority_queue<type , Container , Compare>` 의 형태를 띄며 defalut 구현체 컨테이너는 vector , 비교는 less 를 써서 max_heap 의 형태이다.
- 구조체, 클래스,pair<> 등도 type으로  사용 될 수 있다. //`ex) p_q< pair<int,int> > pq;`


### 사용법

```c++
#include <iostream>
#include <queue>
using namespace std;

typedef struct info {
	int y, x,cnt;
	info(int _y, int _x, int _cnt) :
		y(_y), x(_x),cnt(_cnt) {};
	bool operator <(info A)const { return cnt > A.cnt; } 
	//정렬방법 1. 사용한 구조체 내에 operator 변경

}info;
/*	/
struct cmp {
	bool operator()(info t, info u) {
		return t.cnt > u.cnt;
	}
};	// 정렬방법 2. 새로운 '비교용' 구조체를 만들고 여기에 operator 변경 후 
	// priorty queue 선언시 사용한다.
*/

int main(){
	priority_queue<int> pq;	 //default로 max_heap 
	priority_queue<int,vector<int>,greater<int> > pq2; // min_heap

	priority_queue<info> q;				//방법1
//	priority_queue<info, vector<info>, cmp > q;	//방법2


	pq.push(3);
	pq.push(1);
	pq.push(8);
	pq.push(3);
	pq.push(2);

	cout << pq.top() << endl; // 8 출력
	pq.pop(); // 가장 상위 노드 제거

	cout << pq.top() << endl; // 3 출력

	pq.empty(); // 현재 원소들이 존재하므로 false(1) 반환

	while(!pq.empty()){
		cout << pq.top() << endl;
		pq.pop();
	}

	pq2.push(3);

	cout << pq2.size() << endl; // 원소의 갯수 반환

	return 0;
}
```

- `priority_queue<int (,vector<int>) (, greater<int>/less<int>) > pq` : 두번째 인자인 구현체와 세번째 인자인 비교함수를 설정해 줄 수 있다. compare하는 함수에서 less 가 default 이며 max_heap을 만들고, greater 이 min_heap을 만든다. 유의할 것.
- empty() : 비어 있으면 true 반환
- size() : 원소의 갯수 반환
- top() : 트리의 가장 상위 원소, 루트를 반환
- pop() : 루트를 제거한다. 내부적으로는 다시 힙 정렬을 해서 우선순위 큐를 유지한다
- push(contents) : 인자를 우선순위 큐 안으로 넣는다. 내부적으로 알아서 정렬된다
- ++ 구조체를 사용하여 구현할 때, 우선순위를 지정할 변수를 지정해서 정렬할 수 있다. operator를 업데이트해서 사용.

