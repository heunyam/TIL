# closer(클로저)

- 두개의 파라미터를 받고 곱한 값을 반환하기
- 단 두개의 파라미터를 한꺼번에 받을 수 없음

## class로 해결하는 방법

```python
class Mul:
    def __init__(self, m):
        self.m = m

    def __call__(self, n): # 객체를 함수처럼 호출할 수 있음
        return self.m * n

if __name__ == "__main__":
    mul3 = Mul(3)
    mul5 = Mul(5)

    print(mul3(10)) # 30
    print(mul5(10)) # 50
```

## closer로 해결하는 방법

```python
def mul_of(m):
    def mul(n):
        return m * n
    return mul

if __name__ == "__main__":
    mul3 = mul_of(3)
    mul5 = mul_of(5)

    print(mul3(10)) # 30
    print(mul5(10)) # 50
```

1. mul_of 함수는 mul 함수를 리턴하는 함수이다.
2. 이때 리턴되는 mul 함수는 mul_of 함수를 호출할 때 받은 m값이 mul 함수에 저장된다
3. 이것은 마치 클래스가 특정한 값을 설정하여 객체를 만들어 내는 과정과 거의 흡사하다.

결론: closer는 간단한 경우라면 class에 대한 대체제로 더 우아한 코드를 작성할 수 있다. 