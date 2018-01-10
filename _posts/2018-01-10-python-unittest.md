---
layout: post
title: python unittest
categories:
- etc
tags: Python, programming
commnets: true
---

단위 테스트. PyUnit 이라고 하는 unittest 모듈을 이용.

### Rules

- 테스트를 수행할 클래스는 반드시 unittest.TestCase 상속.
- 클래스 안에 test로 시작하는 멤버 메소드를 구현.
- 메소드 안에 assert~로 시작하는 함수로 테스트 결과를 확인.
- 그 후 unittest.main() 호출시 테스트 수행.


```python
import unittest

def sum(a,b):
	return a+b 

class Module1Test(unittest.TestCase): # unittest.TestCase 상속
	def testSum1(self):
		self.assertEqual(sum(1,2),3)
	def testSum2(self):
		self.assertEqual(sum(1,-1),0)

unittest.main()
```


### 자주 사용하는 assert~ 함수들

|함수명|설명|
|---|---|
|assertEqual(first,second,[msg])|first,second가 같은지 확인, 실패시 msg 출력|
|assertNotEqual(first,second,[msg])|first,second가 다른지 확인, 실패시 msg 출력||
|assertTrue(expr,[msg])|expr이 True인지 테스트|
|assertFalse(expr,[msg])|expr이 False인지 테스트|

### 클래스를 입력받는 unittest

- basicfuction.py
```python
class BasicFunction(object): 
	def __init__(self): 
		self.state = 0

	def increment_state(self): 
		self.state += 1

	def clear_state(self): 
		self.state = 0
```

- test.py

```python
import unittest
from basicfunction import BasicFunction
 
class TestBasicFunction(unittest.TestCase):
	def setUp(self):	# 테스트가 수행되기 전에 테스트 환경을 설정함
		self.func = BasicFunction()
	
	def tearDown(self):	# 테스트 수행 후 테스트 환경을 정리하는 역할
		pass

	def test_1(self):
		self.assertTrue(True)

	def test_2(self):
		self.assertTrue(True)

	def test_3(self):
		self.assertEqual(self.func.state, 0)

	def test_4(self):
		self.func.increment_state()
		self.assertEqual(self.func.state, 1)

	def test_5(self):
		self.func.increment_state()
		self.func.increment_state()
		self.func.clear_state()
		self.assertEqual(self.func.state, 0)

if __name__ == '__main__':
	unittest.main()
```

```
python test.py -v 커맨드로 명령어 실행
```
