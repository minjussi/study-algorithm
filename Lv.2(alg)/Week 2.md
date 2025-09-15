## JadenCase 문자열 만들기

- 모든 단어의 첫 번째 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열 (단, 첫 번째 문자가 알파벳이 아닐 때는 이어지는 알파벳을 소문자로 쓰면 된다.)

- 아스키 코드를 활용해서 소문자->대문자는 -32, 대문자->소문자는 +32로 계산한다. 또, 공백은 아스키 코드 값으로 32이므로 이를 활용한다.

```python
def solution(s):
    answer = ''
    for i in range(len(s)):
        ch = ord(s[i])
        if i == 0:
            if (ch >= 97):
                ch -= 32
        else:
            if (ord(s[i-1])==32):
                if (ch>=97 and ch<=122):
                    ch -= 32
            else:
                if (ch>=65 and ch<=90):
                    ch += 32
        answer += chr(ch)
        
    return answer
```

### 보완해야할 점

- 아스키 코드 값을 활용한 풀이는 좋지만, 중첩 if문이 많고 97, 122, 65, 90 등의 숫자가 무엇을 의미하는지 드러나지 않아 가독성이 떨어진다. 

- 해당 언어는 python이기 때문에 c 스타일로 작성하는 것도 좋지만, python에 특화된 방식으로 작성해보는 것도 좋을 것 같다. 

### 다른 사람 풀이 (출처: 프로그래머스)

- 파이썬에는 title()이라는 내장 함수가 존재하기 때문에 이를 활용하면 코드 길이를 축소시킬 수 있다.

- 숫자가 맨 처음에 오는 경우에 대해서만 숫자 다음 문자를 소문자로 그대로 쓰는 로직을 추가해 주면 모든 테스트케이스를 통과할 수 있다. 

```python
def Jaden_Case(s):
    return s.title()
```

- 밑의 코드가 python의 강점을 잘 살리면서도 가독성이 높은 코드에 가깝다. (capitalize 함수도 사용 가능)

- 문자열을 공백을 기준으로 나누고, 각 단어마다 **[i]** 첫 번째 문자 **[0]** 는 대문자로 바꾸고, 나머지 **[1:]** 부분은 소문자로 바꾼다. 그 다음 각 단어를 answer 리스트에 넣고, 마지막에 단어마다 공백을 넣어 합친 문자열을 반환한다.

```python
def Jaden_Case(s):
    answer =[]
    for i in range(len(s.split())):
        answer.append(s.split()[i][0].upper() + s.split()[i].lower()[1:]) 
    return " ".join(answer)
```
