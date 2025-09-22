## 피보나치 수

> 참고자료
> https://shoark7.github.io/programming/algorithm/%ED%94%BC%EB%B3%B4%EB%82%98%EC%B9%98-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98%EC%9D%84-%ED%95%B4%EA%B2%B0%ED%95%98%EB%8A%94-5%EA%B0%80%EC%A7%80-%EB%B0%A9%EB%B2%95
> https://velog.io/@_choongyul/%ED%94%BC%EB%B3%B4%EB%82%98%EC%B9%98


**1. 기본 재귀 함수 활용한 풀이 (입력값이 10,000까지라 이 풀이로는 해결 불가)**
   
```python
def fibonacci(n):
  if n < 2:
    return n
  else:
    return fibonacci(n-1) + fibonacci(n-2)
```

- 해당 코드를 살펴보면 불필요한 재귀 호출이 여러 번 반복해서 일어남을 알 수 있다.
- 예를 들어, n=5일 때 fibonacci(4) + fibonacci(3)을 계산하기 위해 fibonacci(4)는 fibonacci(3)+fibonacci(2), fibonacci(2)+fibonacci(1), fibonacci(1)+fibonacci(0)을 호출하고,
  fibonacci(3)은 fibonacci(2)+fibonacci(1), fibonacci(1)+fibonacci(0)을 호출하는 것을 알 수 있다.
- Big-O 계산법으로 O(2^n)의 복잡도를 가진다. (각 노드마다 자식 노드 2개씩 생성)

**2. for문 활용**

```python
```

- 

**3. 동적 계획법**



**4. 행렬과 분할 정복법**



**5. 일반항 활용**

- 놀랍게도 .. 피보나치 수를 구하는 일반항 존재 ..
<p align="center">
  <img src="https://github.com/user-attachments/assets/c9476952-72de-4840-b4b3-94c66252c82b" width=45% "/>
</p>

```python
```

