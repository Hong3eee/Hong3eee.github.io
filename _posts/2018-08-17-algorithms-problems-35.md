---
layout: post
title: BaekJoon-no.15683 감시
categories:
- Algorithms
tags: algorithms programming brute-force
comments: true
---

### 문제

[문제링크](https://www.acmicpc.net/problem/15683)

체감 난이도(1~5) : 2.5

### 풀이

완전 탐색 문제. 삼성 18년도 상반기 ds 기출문제라고 한다. 입력의 크기, 맵의 크기도 작아서 보자마자 완전탐색인걸 깨닫는 문제. 그러나 구현하기가 까다롭다. 삼성문제들은 다 생각하긴 쉬운데 구현을 마구 꼬아놓은 느낌. 내가 구현한 방식은 이러하다.  첫째, CCTV가 나올때마다 vector에 저장한다.  둘째, 저장한 CCTV의 상,하,좌,우 4가지 경우로 모든 조합을 다 만든다.  셋째, 각 조합을 시뮬레이션하듯 다 만들어서 사각지대(0) 의 갯수를 센다.


```c++
int dy[8] = {1,0,-1,0,1,0,-1,0};// 상하좌우,상하좌우 공간 2배 써서 처리하기 쉽게 했다.
int dx[8] = {0,1,0,-1,0,1,0,-1};

void fill(int y,int x,int direction){ 
	// 좌표를 받아서 direction 방향으로 감시구역을 채워나간다
	while( (0<= y && y < n) && (0<=x && x < m) ){
		if(arr[y][x] == 6)
			break;
		else
			tmp[y][x] = -1;

		y += dy[direction];
		x += dx[direction];
	}
	return ;
}

int simul(){

	init();

	int ret = 0;
	for(int i =0;i<v.size();i++)
	{
		int val,y,x;
		y = v[i].first;
		x = v[i].second;
		val = arr[y][x];

		switch (val){
			case 1:
				fill(y,x,dir[i]);
				break;
			case 2:
				fill(y,x,dir[i]);
				fill(y,x,dir[i]-2);
				break;
			case 3:
				fill(y,x,dir[i]);
				fill(y,x,dir[i]-1);
				break;
			case 4:
				fill(y,x,dir[i]);
				fill(y,x,dir[i]-1);
				fill(y,x,dir[i]-2);
				break;
			case 5:
				fill(y,x,dir[i]);
				fill(y,x,dir[i]-1);
				fill(y,x,dir[i]-2);
				fill(y,x,dir[i]-3);
				break;
		}
	}
	for(int i=0;i<n;i++)
		for(int j=0;j<m;j++)
			if(tmp[i][j] ==0) ret++;
	return ret;
}

void solve(int idx){
	if(idx == v.size()) {
		ans = min(ans,simul());
		return;
	}

	for(int i =4;i<8;i++)
	{
		dir[idx] = i;	// fill 함수에서 -1,-2,-3 으로 방향 판단하므로 공간 2배 주고난 후,
		// 인덱스 4~7 까지 할당.
		solve(idx+1);
	}

}

int main(){
	scanf("%d %d",&n,&m);

	for(int i=0;i<n;i++)
		for(int j=0;j<m;j++)
		{
			scanf("%d",&arr[i][j]);
			if(arr[i][j] != 6 && arr[i][j] != 0)
				v.push_back(make_pair(i,j));
		}

	solve(0);

	printf("%d\n",ans);

	return 0;
}
```


### 배운 점

- 상하좌우 방향 배열을 공간 복잡도 2배 준거 나름 아이디어 센스있었던듯!
- 다른 방법으로 하자면 (idx+1/2/3) % 4 등의 방법으로 구현한 코드도 있었다. 이 또한 좋은듯.
- 완전탐색 구현연습 많이하자.. 푸는 시간 좀 줄이자.
