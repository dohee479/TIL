# Python

## 연산자

```python
+ : 더하기
- : 빼기
* : 곱하기
/ : 나누기  # float 형으로 몫을 return 한다
// : int 형태의 몫을 반환
% : 나머지를 반환
** : 거듭제곱
    
정수와 실수가 연산이 될 경우 int형은 float형으로 변환된다.
```



## 문자열

``` python
'', ""로 둘러쌀 수 있다.

 
#문자열에서 \뒤에 나오는 문자가 특수문자로 취급되기 하고 싶지 않다면, 첫 따옴표 앞에 r을 붙여서 만들 수 있다.
print(r'C:\some\name')
>>> C:\some\name
    
# 문자열은 + 연산자로 이어붙이고, * 연산자로 반복시킬 수 있다.
print(3 * 'un' + 'ium')
>>> unununium

# 두개 이상의 문자열 리터럴이 연속해서 나타나면 자동으로 이어 붙여집니다.
print('py' 'thon')
>>> python

# 변수끼리 혹은 변수와 문자열을 이어붙이려면 +를 사용해야한다.
prefix = py
print(prefix + 'thon')
>>> python

# 문자열은 인덱싱과 슬라이싱이 가능하다.
# 슬라이싱은 인덱스가 문자들 사이의 위치를 가리킨다고 생각을 한다.
# 왼쪽에서 오른쪽 방향으로의 슬라이싱만 가능, [-4: -6]은 불가능
# 음의 인덱스가 아닌 경우, 슬라이스의 길이는 인덱스 간의 차
| p | y | t | h | o | n |
0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1

# 파이썬의 문자열은 변경할 수 없다, 불변(immutable)이라고 한다.
# 문자열의 인덱스로 참조한 위치에 대입하려고 하면 에러
word = 'python'
word[0] = 'j'
word[2:] = 'py'
>>> 'str' object does not support item assignment

# 다른 문자열이 필요하면, 새로 만들어야한다.
'j' + word[1:]

# len()을 통해 문자열의 길이를 알 수 있다.
```



## 리스트

```python
# 문자열처럼 인덱싱과 슬라이싱이 가능하다.
# 모든 슬라이스 연산은 요청한 항목들을 포함하는 새 리스트를 돌려줍니다. => 얕은 복사
squares = [1, 4, 9, 16, 25]
print(id(squares))
print(id(squares[:]))
>>> 140701266529864
	140701171155336

# +를 통해 이어붙이기가 가능하다.
squares + [36, 49, 64, 81, 100]
>>> [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

# 가변(mutable)하다. 내용을 변경할 수 있다.
# 슬라이스에 대입, 삭제 가능, len() 적용가능
# 결과값은 letter를 print한 값이다.
letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']

# replace some values
letters[2:5] = ['C', 'D', 'E']
>>> ['a', 'b', 'C', 'D', 'E', 'f', 'g']

# now remove them
letters[2:5] = []
['a', 'b', 'f', 'g']

# clear the list by replacing all the elements with an empty list
letters[:] = []
>>> []

# 리스트는 중첩도 가능하다.
a = ['a', 'b', 'c']
n = [1, 2, 3]
x = [a, n]
print(x)
>>> [['a', 'b', 'c'], [1, 2, 3]]
print(x[0])
>>> ['a', 'b', 'c']
print(x[0][1])
>>> b
```



## 제어 흐름도구

### if 문

```python
# 조건문
if , elif, else 

if x < 0:
    pass
elif x == 0:
    pass
else:
    pass
```

### for 문



