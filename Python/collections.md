# collections

## Counter

-  데이터의 개수를 셀 때 사용한다.

```python
from collections import Counter

a = Counter('hello world')
print(a)
# 딕셔너리로 반환
>>> Counter({'l': 3, 'o': 2, 'h': 1, 'e': 1, ' ': 1, 'w': 1, 'r': 1, 'd': 1})

# 데이터의 개수가 많은 순으로 정렬된 배열을 리턴하는 most_common
a = Counter('hello world').most_common()
print(a)
>>> [('l', 3), ('o', 2), ('h', 1), ('e', 1), (' ', 1), ('w', 1), ('r', 1), ('d', 1)]

# most_common에 k 인자를 넘기면 값만큼 반환
a = Counter('hello world').most_common(2)
print(a)
>>> [('l', 3), ('o', 2)]
```

