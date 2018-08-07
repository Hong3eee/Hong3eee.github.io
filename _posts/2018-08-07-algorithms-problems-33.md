---
layout: post
title: BaekJoon-no.12100 2048 easy
categories:
- Algorithms
tags: algorithms programming brute-force
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/12100)

체감 난이도(1~5) : 2.5

### 풀이

				   완전 탐색 문제. 혹자는 dfs라고 말하던데 그 보다는 완전탐색이라고 하는게 좀 더 나은 분류라고 생각한다. 문제 이해도 쉽고 설계또한 쉬운편이다. 그러나 구현하는데 있어서 좀 애를 먹었다. 시간을 너무 많이 잡아먹은 문제. merge 하는 부분에서 queue를 쓴 것과 상하좌우 모든 경우를 다 돌아보는 부분을 구현하면 끝.


```c
case 4: // top
	for(int k=0;k<n;k++)
		for(int j=0;j<n;j++)
	{
		if(arr[j][k] !=0)
			q[k].push(arr[j][k]);
		arr[j][k] = 0;
	}

	for(int j=0;j<n;j++)
	{
		idx = 0;
		while(!q[j].empty()){
			int tmp = q[j].front();
				q[j].pop();
	
			if(arr[idx][j] == 0) arr[idx][j] = tmp;
			else if(arr[idx][j] == tmp){
				arr[idx][j] = tmp *2;
				idx++;
			}
			else arr[++idx][j] = tmp;
		/* 큐 처음 생각해서 구현한 부분. 여기서 segmentation fault 가 떠서 바꿈
		   if(tmp == q[j].front())
		   {
		   arr[idx][j] = tmp * 2;
		   idx++;
		   q[j].pop();
		   }
		   else
		   {
		   arr[idx][j] = tmp;
		   idx++;
		   }
		 */
		}
	}
	break;
```
### 배운 점

- 설계는 매우 쉬운편이나 구현에서 막혀서 좀 많이 귀찮았던 문제. 그래도 구현속도를 좀 올려야 할 필요성을 느꼈다. 코테에서 시간은 제한적이니깐.
- 각 행 혹은 열마다 병합을 해줘야하는데 일렬로 쭈욱 늘어져 있는 이런 경우엔 큐를 쓰면 매우 유용한 듯 하다.
- 어제 푼 문제가 메모리 부족이 떠서 배열을 복사해서 넘긴 게 아니라 배열은 전역으로 두고, 인덱스만 가지고 넘겼었다. 이 것도 참고하자. 문제는 백준 2263번 문제.
