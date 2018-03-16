---
layout: post
title: re , queue module
categories:
- etc
tags: Python programming
commnets: true
---

파이썬 프로그래밍에 유용한 모듈.

## re 정규표현식 모듈

정규표현식은 특정한 규칙을 가진 문자열을 표현하는데 사용되는 형식 언어이다.  

|함수명|설명|
|---|---|
|re.search(pattern,string[,flags])|string에 pattern이 존재하는지 검색 후 match 인스턴스 반환|
|re.match(pattern,string[,flags])|string맨 처음부터 pattern이 존재하면 match 인스턴스 반환|
|re.split(pattern,string[,maxsplit=0])|pattern을 구분자로 string을 분리해 리스트로 반환|
|re.findall(pattern,string[,flags])|string에서 pattern과 매치되는 것들을 리스트로 반환|
|re.finditer(pattern,string[,flags])| "" 이터레이터 객체로 반환|
|re.sub(pattern,repl,string[,count])|string에서 pattern과 일치하는 부분에 대해 repl로 교체해서 결과 문자열을 반환|
|re.subn(pattern,repl,string[,count])| "" (결과 문자열,매칭 횟수)를 튜플로 반환|
|re.escape(string)|영문자,숫자가 아닌 문자에 대해 백슬래시 문자를 추가|
|re.compile(pattern[,flags])|pattern을 컴파일해서 정규표현식 객체로 반환|


```python
bool(re.match('[0-9]*th;,'35th'))	# match 객체 반환
-> True
bool(re.search('[0-9]*th;,'35th'))
-> True
bool(re.match('[0-9]*th;,'     35th'))	# match는 맨앞부터 비교시작
-> False
bool(re.search('[0-9]*th;,'     35th'))
-> True
```

```python
re.split('[:. ]+','apple Orange:banana tomato')	# split
-> ['apple','Orange','banana','tomato']

re.findall(r"app\w*","application orange apple banana") # findall
-> ['application','apple']

re.sub("-","","820101-1234567") # sub
-> '8201011234567'
```

- re.compile()

동일한 패턴을 연속적으로 검색할 경우 정규식을 반복해서 써야하므로 비효율적임.  
효율적으로 하고자 compile()을 이용하여 정규표현식 객체를 생성.
```python
re.findall(r"app\w*","application orange apple banana") # findall
re.findall(r"app\w*","there are many apples") # findall

c = re.compile(r"app\w*")	# re. 대신에 c.함수명 으로 사용
c.findall("application orange apple banana")	# 같은 결과 반환
c.findall("there are many apples")
```

### match 객체

- 검색된 결과를 효율적으로 처리할 수 있는 기능 제공
- match(), search()의 수행결과로 생성

```python
m = telChecker.match('012-3456-7890')
m.groups()	# 문자열 집합을 튜플로 반환
-> ('012','3456','7890')
m.group()	# 문자열 반환
-> '012-3456-7890'
m.start() 	# 문자열 시작 인덱스
-> 0
m.end()		# 문자열 전체의 마지막 인덱스
-> 13
m.string	# 매칭의 대상이 되는 원본 문자열
-> '012-3456-7890'
```

## queue 모듈

널리 쓰이는 자료구조인 큐 & 스택을 제공하는 모듈.

|클래스|설명|
|---|---|
|queue.Queue(maxsize)|FIFO 큐 객체 생성|
|queue.LifoQueue(maxsize)|LIFO (스택) 객체 생성|
|queue.PriorityQueue(maxsize)|우선순위 큐 객체 생성. 입력되는 데이터는 (순위,아이템)의 튜플로 입력되며, 숫자가 작을수록 순위가 높다.|

```python
q = queue.Queue()
q.put("apple")
q.put("banana")
q.put(10)
q.qsize()
-> 3
q.get()
-> "apple"
q.get()
-> "banana"
```
