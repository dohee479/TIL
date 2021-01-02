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

```python
# 임의의 시퀀스(리스트나 문자열)의 항목들을 그 시퀀스에 들어있는 순서대로 이터레이션한다.
# 컬렉션을 이터레이트 하는 동안 같은 컬렉션을 수정하는 코드는 올바르게 동작하도록 만들기 힘들다.
# 보통 컬랙션의 복사본으로 루프를 만들거나 새 컬렉션을 만드는 것이 더 간단하다.

# Strategy:  Iterate over a copy
for user, status in users.copy().items():
    if status == 'inactive':
        del users[user]

# Strategy:  Create a new collection
active_users = {}
for user, status in users.items():
    if status == 'active':
        active_users[user] = status
```



### range() 함수

```python
# 숫자들의 시퀀스로 이터레이트해야한다면, 내장함수 range() 사용한다.
# 끝 값은 만들어지는 수열에 포함되지 않는다.
for i in range(5):
    pass

# 시퀀스의 인덱스들로 이터레이트 하려면, range()와 len()을 결합
for i in range(len(a)):
    pass

# 하지만, 대부분 enumerate() 함수를 쓰는 것이 편리

# 많은 경우에 range()가 돌려준 객체는 리스트인 것처럼 동작하지만, 사실 리스트가 아니다.
# 이터레이트 할 때, 시퀀스 항목들을 순서대로 돌려주는 객체이지만, 실제로 리스트를 만들지 않아 공간 절약한다. 이런 객체를 이터러블이라고 부른다.
# 공급이 소진될 때까지 일련의 항목들을 얻을 수 있는 무어잇가를 기대하는 함수와 구조물들의 타깃으로 적합
# ex) sum()

# range()에서 리스트를 얻는 방법
list(range(4))
```



###  루프의 break와 continue, 그리고 else절

```python
# break는 가장 가까이서 둘러싸는 for나 while 루프로부터 빠져나가게 한다.

# 루프 문은 else 절을 가질 수 있다. 루프가 이터러블의 소진이나 조건이 거짓되서 종료할 때 실행된다.
# 하지만 루프가 break문으로 종료할 때는 실행되지 않습니다.
for n in range(2, 10):
     for x in range(2, n):
         if n % x == 0:
             print(n, 'equals', x, '*', n//x)
             break
     else:
         # loop fell through without finding a factor
         print(n, 'is a prime number')
        
# continue 루프의 다음 이터레이션에서 계속하도록 한다.
```



### pass 문

```python
# pass 문은 아무것도 하지 않는다. 자리를 채우는 용도이다.
while True:
    pass

class MyEmptyClass:
    pass
```



### 함수 정의하기

```python
def fib(n):    # write Fibonacci series up to n, n은 매개변수
     """Print a Fibonacci series up to n."""
     a, b = 0, 1
     while a < n:
         print(a, end=' ')
         a, b = b, a+b
     print()

# def로 함수 정의를 시작한다.
# 함수 바디의 첫 번째 문장은 선택적으로 문자열 리터럴이 될 수 있다. 독스트링이다.

# 함수의 실행은 지역 변수를 위한 새 심볼 테이블을 만들고, 모든 변수 대입들은 지역 심볼 테이블에 저장된다.
# 변수 참조는 지역 -> 전역 -> 내장이름의 테이블 순이다.
# 인자들은 값에 의한 호출(call by value)로 전달된다. (값은 객체의 값이 아니라 객체 참조이다.)

# call by value : 함수의 인자를 받을 때, 인자의 자체(주소 값)가 이나라 복사값이다.
# call by refernce : 인자를 받을 때, 주소 값을 전달한다. 원본 전역 변수의 주소값

# python에서 변수는 특정 메모리 공간을 할당 받는 개념이 아니라, 객체의 이름표일 뿐이다.
a = 1
b = 1
c = 1
>>> 3개의 변수의 주소를 출력하면 모두 같다.

# 정확히 보자면 call by objective-reference 방식이다.
# immutable 한 포맷의 객체(tuple 등)는 변경할 수 없지만,
# mutable한 포맷의 객체(list, dictionary, 직접 만든 클래스 등)는 변경할 수 있다는 특성을 갖는다.
```



### 함수 정의 더 보기

```python
# 기본 인자값

# 가정 쓸모 있는 형식은 하나나 그 이상의 인자들의 기본값을 지정하는 것입니다.
# 정의된 것보다 더 적은 개수의 인자들로 호출될 수 있는 함수를 만든다.

def ask_ok(prompt, retries=4, reminder='Please try again!'):
    while True:
        ok = input(prompt)
        if ok in ('y', 'ye', 'yes'):
            return True
        if ok in ('n', 'no', 'nop', 'nope'):
            return False
        retries = retries - 1
        if retries < 0:
            raise ValueError('invalid user response')
        print(reminder)
        
# 꼭 필요한 인자만 전달해서: ask_ok('정말 끝내길 원하세요?')
# 선택적 인자 하나를 제공: ask_ok('파일을 덮어써도 좋습니까?', 2)
# 모든 인자를 제공: ask_ok('파일을 덮어써도 좋습니까?', 2, '자, 예나 아니요로만 답하세요!')
```

```python
# 기본값은 오직 한번만 구해지는데, 기본값이 mutable하면 차이가 생긴다. 계속되는 호출로 전달된 인자 누적
def f(a, L=[]):
    L.append(a)
    return L

print(f(1))
print(f(2))
print(f(3))

>>> [1]
>>> [1, 2]
>>> [1, 2, 3]
```



### 키워드 인자

```python
# *args는 임의로 정한 변수이름, 입력값의 개수는 상관 x, 입력값을 모아 전부 튜플로 만들어 준다.
# add_many(1 ,2, 3) -> args = (1, 2, 3)

def add_many(*args): 
    result = 0 
    for i in args: 
        result = result + i 
    return result


# **kwargs는 딕셔너리 형태로 만들어진다.
# print_kwargs(a=1) -> {'a': 1}

def print_kwargs(**kwargs):
    print(kwargs)
```



### 위치 키워드 인자

```python
# /, * 가 없으면,인자를 위치나 키워드로 함수에 전달할 수 있습니다.

# 위치, 키워드 둘다 가능
def standard_arg(arg):
    print(arg)

# 위치만 가능
def pos_only_arg(arg, /):
    print(arg)

# 키워드만 가능
def kwd_only_arg(*, arg):
    print(arg)
```



### 람다 표현식

```python

```



### docstring

```python
# docstring은 모듈, 함수, 클래스 또는 메소드 정의의 첫 번째 명령문으로 발생하는 문자열 리터럴
# Module 첫번째 줄, 함수 선언 후 내부 바로 아랫줄 또는 클래스 선언 후 내부 바로 아랫줄에 큰따옴표 3개나 작은 따옴표 3개로 작성한다.

def fetch_words(url):
    """
    url주소에서 파일을 가져와 단어 리스트를 반환합니다.
    :param url: 불러올 url
    :return:
    """
    with urlopen(url) as story:
        story_words = []
        for line in story:
            line_words = line.decode('utf-8').split()
            for word in line_words:
                story_words.append(word)
    return story_words
... 생략


from words import fetch_words
print(help(fetch_words))

from words import fetch_words
print(fetch_words.__doc__)
>>> '\n    url주소에서 파일을 가져와 단어 리스트를 반환합니다.\n    :param url: 불러올 url\n    :return:\n    '
```



### 코딩 스타일

- 들려 쓰기에 4-스페이스를 사용하고, 탭을 사용하지 마세요.
- 79자를 넘지 않도록 줄 넘김 하세요.
  - 이것은 작은 화면을 가진 사용자를 돕고 큰 화면에서는 여러 코드 파일들을 나란히 볼 수 있게 합니다.
- 함수, 클래스, 함수 내의 큰 코드 블록 사이에 빈 줄을 넣어 분리하세요.
- 가능하다면, 주석은 별도의 줄로 넣으세요.
- 독스트링을 사용하세요.
- 연산자들 주변과 콤마 뒤에 스페이스를 넣고, 괄호 바로 안쪽에는 스페이스를 넣지 마세요: `a = f(1, 2) + g(3, 4)`.
- 클래스와 함수들에 일관성 있는 이름을 붙이세요; 관례는 클래스의 경우 `UpperCamelCase`, 함수와 메서드의 경우 `lowercase_with_underscores`입니다. 첫 번째 메서드 인자의 이름으로는 항상 `self`를 사용하세요



## 자료구조

### 리스트 더보기

- `l.append(x)`: 리스트 끝에 항목을 더함.
  - `l[len(l):] = [x]`  와 동등
  - O(1)
- `l.extend(iterable)`: 리스트 끝에 이터러블의 모든 항목을 덧붙여서 확장
  - `l[len(l):] = iterable`  와 동등
  - O(len(...)) (확장되는 길이만큼)
- `l.insert(i, x)`: i의 위치에 x를 삽입
  - O(N)
- `l.remove(x)`: 리스트에서 값이 x와 같은 첫번째 항목을 삭제, 없으면 valueError
  - O(N)
- `l.pop(i)`: i의 위치에 있는 항목 삭제, 그 항목을 돌려준다.
  - i가 있는 경우: O(n)
  - i가 없는 경우: O(1)
- `l.clear()`: 리스트의 모든 항목을 삭제
  - `del l[:]` 과 동일
  - O(1)
- `l.index(x)`: x와 같은 첫번째 항목의 index를 돌려준다. 없으면 valueError
  - `l.index(x, start, end)`: start, end 사이로 범위를 주어 그사이에 x의 index값을 찾게 할 수 있다.
  - O(N)
- `l.count(x)`: 리스트에서 x가 등장하는 횟수를 돌려준다.
  - O(N)
- `l.sort(*, key=None, reverse=False)`: 리스트의 항목들을 제자리에서 정렬
  - O(N log N)
- `l.reverse()`: 리스트의 요소들을 제자리에서 뒤집는다. 정렬없이 뒤집기만 한다.
  - O(N)
- `l.copy()`: 리스트의 얕은 사본을 돌려줍니다.
  - 얕은 복사, 깊은 복사( https://wikidocs.net/16038 참조)
  - `l[:]` 와 동등
  - O(N)



### 리스트를 스택으로 사용하기

```python
# last-in, first-out
# stack 꼭대기에 append()를 사용하여 항목넣기, 값을 꺼내려면 pop() 사용
```



### 리스트를 큐로 사용하기

```python
# first-in, first-out
# 리스트를 큐로 사용하는 것도 가능하나, 효율적이지 않다.
# 끝에 덧붙이거나 꺼내는 것은 빠르나, 머리에 붙이거나 꺼내는 것은 느리다.(다른 요소들이 한칸씩 이동하기 때문)
# deque 사용을 권장한다.
```



### 리스트 컴프리헨션

```python
# 리스트를 만드는 간결한 방법
# x 라는 이름의 변수를 만들고 (또는 덮어쓰고) 루프가 종료된 후에도 남아있게 만든다는 것에 유의

sqares = []
for x in range(10):
    squares.append(x**2)

# 위에 식을 이렇게 할 수 있다.
squares = list(map(lambda x: x**2, range(10)))
squares = [x**2 for x in range(10)]

[(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
>>> [(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```



### 중첩된 리스트 컴프리헨션

```python
[[row[i] for row in matrix] for i in range(4)]
>>> [[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```



### del 문

```python
# 리스트에서 값 대신 인덱스를 사용하여 항목을 삭제하는 방법
a = [-1, 1, 66.25, 333, 333, 1234.5]

del a[0]
a
>>> [1, 66.25, 333, 333, 1234.5]
del a[2:4]
a
>>> [1, 66.25, 1234.5]
del a[:]
a
>>> []
```



### 튜플과 시퀀스

```python
# 튜플은 리스트처럼 보이나, immutable하다.
# 튜플은 소괄호로 쌓여있다.

t = 12345, 54321, 'hello!'
t[0]
>>> 12345

t
>>>(12345, 54321, 'hello!')

# Tuples may be nested:
u = t, (1, 2, 3, 4, 5)
u
>>>((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
```



### 집합

```python
# 중복되는 요소가 없는 순서 없는 컬렉션, 주 목적은 중복 엔트리 제거, 합집합, 교집합 등 수학적 연산
# set()을 통하여 생성
# 리스트 컴프리 헨션과 유사하게, 집합 컴프리헨션도 지원
a = {x for x in 'abracadabra' if x not in 'abc'}
a
>>> {'r', 'd'}
```



### 딕셔너리

```python
# 키로 인덱싱, 모든 불변형 사용가능, 문자열과 숫자들은 항상 키가 될 수 있다.
# {}, dict()로 생성가능, dict()는 키-값 쌍들의 시퀀스로부터 직접 딕셔너리 구성
dict([('sape', 4139), ('guido', 4127), ('jack', 4098)])
>>> {'sape': 4139, 'guido': 4127, 'jack': 4098}

# 키가 간단한 문자열일 때, 키워드 인자을 사용 지정하기 쉽다.
dict(sape=4139, guido=4127, jack=4098)
>>>{'sape': 4139, 'guido': 4127, 'jack': 4098}

# del로 키:값 쌍 삭제 가능
del tel['sape']

# 딕셔너리 컴프리헨션 가능
{x: x**2 for x in (2, 4, 6)}
>>> {2: 4, 4: 16, 6: 36}
```



### 루프 테크닉

```python
# items 메서드 사용하면 키와 대응 값을 동시에 얻을 수 있다.
knights = {'gallahad': 'the pure', 'robin': 'the brave'}
for k, v in knights.items():
    print(k, v)
    
>>> gallahad the pure
>>> robin the brave

# 시퀀스 루핑할 때, enumerate()를 사용하면 인덱스와 대응하는 값을 동시에 얻을 수 있다.
for i, v in enumerate(['tic', 'tac', 'toe']):
    print(i, v)
    
>>> 0 tic
>>> 1 tac
>>> 2 toe

# 둘이나 그 이상의 시퀀스를 동시에 루핑하려면, zip() 함수로 엔트리들의 쌍을 만들 수 있다.
list(zip([1, 2, 3], [4, 5, 6]))
>>> [(1, 4), (2, 5), (3, 6)]

# 거꾸로 루핑
for i in reversed(range(1, 10, 2)):
    print(i)
    
# 정렬 
for i in sorted(basket):
    print(i)
    
# 중복제거
for i in sorted(set(basket)):
    print(i)
```



### 시퀀스와 다른 형들을 비교하기

- 비교는 사전식 순서를 사용한다.
- 먼저 첫 두 항목을 비교, 다르면 비교의 결과를 결정, 같으면 다음 두 항목을 비교

```python
[1, 2, 3]              < [1, 2, 4]
'ABC' < 'C' < 'Pascal' < 'Python'
(1, 2, 3, 4)           < (1, 2, 4)
(1, 2)                 < (1, 2, -1)
(1, 2, 3)             == (1.0, 2.0, 3.0)
(1, 2, ('aa', 'ab'))   < (1, 2, ('abc', 'a'), 4)
```



## 모듈

```python
# 모듈을 사용하는 방법
import fibo

from fibo import fib

# 모듈 이름 다음에 as가 올 경우, as 다음의 이름을 임포트한 모듈에 직접 연결한다.
import fibo as fib 
fib.fib(500)

# from을 써서 비슷한 효과를 낼 때도 사용가능하다.
from fibo import fib as fibonacci
fibonacci(500)
```



## 입력과 출력

- 값을 쓰는 두가지 방법

  - 표현식 문장

  - print() 함수

  - 세 번째 방법: 파일 객체의 write() 메서드 사용, 표준 출력 파일은 sys.stdout로 참조

    

- 장식적인 출력 필요 X, 단지 디버깅 위해 일부 변수 빠르게 표시

  - ```python
    # repr()
    s = 'Hello'
    print(repr(s))
    >>> 'Hello'
    
    # str()
    print(str(s))
    >>> Hello
    ```



- 포맷 문자열 리터럴(f-문자열)

```python
# 문자열에 f or F 접두어 붙이고 표현식을 {expression}
print(f'The value of pi is approximately {math.pi:.3f}.')

# : 뒤에 정수를 전달하면 해당 필드의 최소 문자 폭이 된다.
table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 7678}
for name, phone in table.items():
print(f'{name:10} ==> {phone:10d}')
>>>
Sjoerd     ==>       4127
Jack       ==>       4098
Dcab       ==>       7678

# !a 는 ascii()를 !s는 str() !r는 repr() 적용
 print(f'My hovercraft is full of {animals!r}.')
```



- 문자열 format() 메서드

```python
# str.format()
print('We are the {} who say "{}!"'.format('knights', 'Ni'))

# 나누고 싶지 않은 정말 긴 포맷 문자열이 있을 때, 포맷할 변수들을 위치 대신에 이름으로 지정할 수 있다면 좋을 것입니다. 간단히 딕셔너리를 넘기고 키를 액세스하는데 대괄호 '[]' 를 사용하면 됩니다.
table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 8637678}
print('Jack: {0[Jack]:d}; Sjoerd: {0[Sjoerd]:d}; '
      'Dcab: {0[Dcab]:d}'.format(table))
>>> Jack: 4098; Sjoerd: 4127; Dcab: 8637678
            
# <**> 표기법을 사용해서 table을 키워드 인자로 전달해도 같은 결과를 얻을 수 있습니다.
print('Jack: {Jack:d}; Sjoerd: {Sjoerd:d}; Dcab: {Dcab:d}'.format(**table))
>>> Jack: 4098; Sjoerd: 4127; Dcab: 8637678
```



- 수동 문자열 포매팅

  - str.rjust()  : 왼쪽에 스페이스를 채워서 주어진 폭으로 문자열을 우측 줄 맟춤, ljust(), center()도 있다.

  - str.zfill() : 숫자 문자열의 왼쪽에 0을 채운다.

  - ```python
    '12'.zfill(5)
    >>> '00012'
    
    '-3.14'.zfill(7)
    >>> '-003.14'
    
    '3.14159265359'.zfill(5)
    >>>'3.14159265359'
    ```

    

### 파일을 읽고 쓰기

- open() :  파일 객체를 돌려주고, 두 개의 인자를 주는 방식이 가장 많이 사용

```python
open(filename, mode)

f = open('workfile', 'w')
```

- mode : 선택적인데, 생략하면 `r`이 가정된다.
  - r : 파일 읽기
  - w : 쓰기 (같은 이름의 이미 존재하는 파일은 삭제된다.)
  - a : 파일을 덧붙이기 위해 연다, 파일에 기록되는 모든 데이터는 자동으로 끝에 붙는다.
  - r+ : 파일을 읽고 쓰기 위해 연다.
- https://docs.python.org/ko/3.9/tutorial/inputoutput.html 참조



## 에러와 예외

- 다양한 에러 존재
  - https://docs.python.org/ko/3.9/library/exceptions.html#bltin-exceptions 참조



- 예외처리

```python
while True:
    # 먼저, try 실행, 예외 발생 하지 않으면, except절 건너뛰고 try 문의 실행은 종료
    try:
        pass
    # 예외 발생시 except 절 실행, 그 다음 try 실행
    except:
        pass
```



- 예외 일으키기

```python
raise NameError('HiThere')
```



- 예외 연쇄
  - https://docs.python.org/ko/3.9/tutorial/errors.html 참조