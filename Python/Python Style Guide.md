# 훌륭한 코드 작성하기

## 코드 스타일

### 명시가 암시가 좋다

```python
# 두 개의 값을 입력 받아 딕셔너리 형태의 결과를 출력하는 예제이다

## 나쁨
def make_dict(*args):
    x, y = args
    return dict(**local())

## 좋음
def make_dict(x, y):
    return {'x': x, 'y': y}
```

### 여유로운 것이 밀집한 것보다 좋다

```python
print('one'); print('two')

print('one')
print('two')
```

```python
if x == 1: print('one')

if x == 1:
	print('one')
```

```python
if ( x.split(' ')[0] == 'asxcasd' and 
   	 y.split('-')[1] == 'asdwefa'):
    # 원하는 작업 수행
    
cond1 = x.split(' ')[0]
cond2 = y.split('-')[1]
if cond1 == 'asxcasd' and cond2 == 'asdwefa':
    # 원하는 작업 수행
```

 최대한 여러 줄로 구분하여 작성해서 가독성을 높인다. 한 줄에는 한 구문씩만 작성해야 한다.

### 오류 앞에서 침묵하지 않는다구

try 구문을 사용해서 오류를 처리한다.

```python
# 다음과 같이 오류처리를 남용하지 말자
while True:
	try:
        print("yeah", end=" ")
    except:
       	pass
    
# 아래와 같이 오류가 발생했음을 알리고 예외를 강제로 raise 하면 상관없다.
while True:
	try:
        print("yeah", end=" ")
    except:
       	print("An exception happened")
        raise
```

예외를 처리하지 않은 `except`구문은 프로그램의 버그를 감춘다.

잡아서 처리하고자 하는 예외만 `except`문에 명시하자



