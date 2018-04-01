---
layout: post
title: BaekJoon-no.11052
categories:
- Algorithms
tags: algorithms programming dp
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/11052)

체감 난이도(1~5) : 2.5

### 풀이

N 번째 칸을 채우는 경우를 생각하자.  
N 번째를 P[N] 한 세트를 파는 경우, D[N-i] + D[i] (1<=i<=N) 정도로 생각할 수 있다. i의 범위가 있으므로 for문을 돌려서 가장 큰 값을 D[N]에 대입!

```c
for(int i=1;i<N+1;i++)
	for(int j=1;j<i+1;j++)
		d[i] = max(d[i],max(p[i],d[i-j]+d[j]));
```

### 배운 점

- [11726](https://hong3eee.github.io/algorithms/2018/03/30/algorithms-problems-6.html) 문제와 거의 비슷하지만 max를 이용한다는 것만 차이남
#### - DP 문제들은 거의 이런 형태란 것을 의식하게 됨. 즉 N번째에 들어가는 점화식을 세우고 그에 대한 증명만 하면 풀린다. 물론 그 점화식 세우는게 어렵기는 하다.
