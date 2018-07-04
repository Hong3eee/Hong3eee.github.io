---
layout: post
title: C++ IO 기초
categories:
- Algorithms
tags: algorithms io input output
comments: true
---

C++ Cin, Cout IO

### Cin

- 공백(스페이스,개행,탭)은 무시하고 읽는다.(처음 입력된 공백 무시)
- 읽을 수 있는 유효한 입력까지만 읽는다.
- 유효한 입력까지 읽고 난 나머지 입력들은 버퍼에 남아서 다음 cin 에서 읽힌다. 이를 주의할 것.
- hex oct dec 조작자manipulator로 x진수를 읽을 수 있다. 조작자를 사용하면 다음 입력부터는 그 형식으로 정수를 읽기 때문에 주의할 것. 
- string 형을 입력 받을 수 있으나, 1줄 전체를 입력받을 순 없다. 공백으로 구분하기 때문.
- 그러므로 getline(cin,(string) var)를 이용해 1줄씩 입력받는다.


```c++
char a;
string str;

cin >> a;
cin >> str;
cout << a << endl;
cout << str << endl;

//1vvasdff 입력 시, 
//
//1
//vvasdff 
//
//출력함

//////////////////////////

cin >> hex >> h;	// 16진수

cin >> dec >> d;	// 10진수

string s;

cin >> s; // string 입력 받음

getline(cin,s); // 1줄 통째로 입력받음
```

### Cout

- printf 와 달리 형에 상관없이 출력해준다.
- 개행을 보통 `endl` 로 하는데 `\n` 로 해도 상관없다. 단, endl은 버퍼에 남아있는 데이터를 flush 하는 기능도 한다.
- cin 과 마찬가지로 hex oct dec 조작자로 x진수 출력을 도와준다.

```c++

cin >> input;

cout << oct << input << endl;
cout << dec << input << endl;
cout << hex << input << endl;
```
