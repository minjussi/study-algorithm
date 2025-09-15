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

### 다른 사람 풀이


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


## 올바른 괄호

- (스택 활용 풀이) 여는 괄호가 들어오면 stack에 push하고, 닫는 괄호가 들어오면 stack에 여는 괄호가 있는지 확인하고 없으면 False를 출력한다. 여는 괄호가 있으면 여는 괄호의 개수와 닫는 괄호의 개수가 일치하는지 확인한다. 마지막으로 stack에 여는 괄호가 남아 있는지 확인한다.

```python
def solution(s):
    stack = []
    answer = True
    for i in range(len(s)):
        if s[i] == "(":
            stack.append(s[i])
            
        elif s[i] == ")":
            if len(stack) == 0:
                answer = False
                return answer
            else:
                stack.pop(-1)
    if len(stack) == 0:
        answer = True
    else:
        answer = False
    return answer
```
