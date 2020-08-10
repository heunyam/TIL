# 데코레이터

- 함수의 수행시간을 출력하고 싶다

```python
import time


def decorate(original_func):   # 기존 합수를 입력으로 받는다.
    def wrapper():
        start = time.time()
        original_func()    # 기존 함수를 수행한다.
        end = time.time()
        print(f"함수 수행시간: {end - start}초")
    return wrapper


def myfunc():
    print("함수가 실행됩니다.")


decorated_myfunc = decorate(myfunc)
decorated_myfunc()
```

1. 클로저를 사용하여 구현하였다. 
2. 파이썬 데코레이터는 @를 이용한 어노테이션을 사용하면 좀 더 간단하게 작성할 수 있다.
3. 데코레이터로 구현해보자

```python
import time


def decorate(original_func):   # 기존 합수를 입력으로 받는다.
    def wrapper():
        start = time.time()
        original_func()    # 기존 함수를 수행한다.
        end = time.time()
        print(f"함수 수행시간: {end - start}초")
    return wrapper

@decorate
def myfunc():
    print("함수 실행됨")

myfunc() 
```

1. 코드가 더 간단해졌다.
2. 이제는 "함수 실행됨" 이 아니라 msg를 따로 받아서 출력하고 싶다.
3. wrapper 함수에 `*args, **kwargs`를 받도록 하자

```python
import time


def decorate(original_func):
    def wrapper(*args, **kwargs):   # *args, **kwargs 입력인수 추가
        start = time.time()
        original_func(*args, **kwargs)  # 전달받은 *args, **kwargs를 입력파라미터로 기존함수 수행
        end = time.time()
        print(f"함수 수행시간: {end - start}초")
    return wrapper


@decorate
def myfunc(msg):
    print(f"{msg}을 출력합니다.")


myfunc("test text")
```

결론: 함수의 앞이나 뒤에 실행시킬 함수를 간편하게 구현할 수 있다. 
