## 최댓값과 최솟값

- 가장 기본적으로 시도해 볼 수 있는 방법은 max와 min을 가장 첫 번째 숫자로 두고, 모든 숫자를 비교해가는 방법이다.

```python
def solution(s):
    array = list(map(int, s.split(' '))) 
    max = array[0]
    min = array[0]
    for i in range(len(array)):
        if max <= array[i]:
            max = array[i]
        elif min >= array[i]:
            min = array[i]
    answer = ""
    answer += str(min) + " " + str(max)
    return answer
```

- 사실 파이썬에는 min, max 내장 함수가 있기 때문에 이걸 사용하면 빠르게 해결할 수 있다.

```python
def solution(s):
    array = list(map(int, s.split(' ')))   
    answer = ""
    answer += str(min(array)) + " " + str(max(array))
    return answer
```

cf) 입력 시간을 빠르게 하는 방법: input 함수를 다른 것으로 바꾼다.

```python
import sys
input = sys.stdin.readline
```
