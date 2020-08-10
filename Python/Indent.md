# 인덴트(Indent) 

공식가이드인 PEP 8에 따라 공백 4칸을 원칙으로 한다.
> 파이썬의 개발은 파이썬 개선 제안서(PEP) 프로세스를 통해 진행된다.
> PEP 프로세스는 새로운 기능을 제안하고 커뮤니티의 의견을 수렴하여
> 파이썬의 디자인 결정을 문서화하는 파이썬의 주요 개발 프로세스를 일컫는다.

## 규칙
```python
foo = long_function_name(var_one, var_two,
                         var_three, var_four)
```
- 첫 번째 줄에 파라미터가 있다면, 파라미터가 시작되는 부분에 보기 좋게 맞춘다.

```python
def long_function_name(
        var_one, var_two,
        var_three, var_four):
    print(var_one)
```
- 첫 번째 줄에 파라미터가 없다면, 공백 4칸 인덴트를 한 번 더 추가하여 구분하도록 한다.

