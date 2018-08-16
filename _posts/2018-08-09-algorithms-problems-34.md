---
layout: post
title: BaekJoon-no.9251 LCS
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/9251)

체감 난이도(1~5) : 2.5

### 풀이

				   그냥 무난한 dp문제. `d[first][second]` 배열을 첫 문자열의 first, 두 번째 문자열의 second 인덱스 까지의 LCS로 놓고 풀면 된다. 문자열을 하나씩 비교해서 `O(n*m)`의 시간복잡도가 나오며, 비교하는 문자열이 같다면 d 배열에서 `d[i-1][j-1] + 1` 로 점화식을 세운다.


```c++
for(int i = 1; i<a.size() ; i++)
for(int j = 1; j<b.size() ; j++)
{
	if(a[i] == b[j])
		d[i][j] = d[i-1][j-1] + 1;
	else
		d[i][j] = max(d[i-1][j] , d[i][j-1]);
}
```


### 배운 점

- 나는 문자열들을 string a,b 로 받아서 이 문자열의 맨 앞에 빈 문자열을 하나 넣어주려고 했으나 쉽지않았다. 그래서 메인 로직 전에 문자열을 처리해주는 선처리 코드를 처리하느라 시간을 조금 잡아먹었다.
- 다른 사람들의 코드를 보니 이 부분을 char형 배열로 받아서 `scanf("%s %s",a+1,b+1);` 로 간단하게 처리한 코드가 있었다. 이 같은 스킬 하나로 시간을 5~10분은 아낄 수 있으니 기억해두자.
