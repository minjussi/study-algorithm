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

