## 아픈 동물 찾기


```sql
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
WHERE INTAKE_CONDITION = 'Sick';
```


## 어린 동물 찾기

```sql
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
WHERE INTAKE_CONDITION != 'Aged';
```

## 이름이 없는 동물의 아이디

```sql
SELECT ANIMAL_ID
FROM ANIMAL_INS
WHERE NAME is NULL;
```

## 경기도에 위치한 식품 창고 목록 출력하기

- NULL이 포함된 값은 'N'으로 출력: IFNULL 함수를 사용해서 NULL 값을 찾은 다음에 해당 attribute는 FREEZER_YN으로 표시될 수 있도록 한다.

- 경기도에 위치한 식품 창고 목록만 출력해야 하기 때문에 문자열에 '경기'가 포함된 값들만 찾는다. (LIKE %'경기'% 구문 사용)

```sql
SELECT WAREHOUSE_ID, WAREHOUSE_NAME, ADDRESS, IFNULL(FREEZER_YN, 'N') AS FREEZER_YN
FROM FOOD_WAREHOUSE
WHERE WAREHOUSE_NAME LIKE '%경기%';
```

## 조건에 맞는 회원 수 구하기

- aggregate functions(집계함수): 행에 대하여 연산을 진행한 다음 요청한 값을 return 해주는 함수이다. (COUNT, SUM, AVG, MIN, MAX 등이 있다.)

- 2021년에 가입했고, 나이가 20세 이상 29세 이하인 회원들을 찾는 쿼리이므로 다음과 같이 작성한다. 

```sql
SELECT COUNT(USER_ID)
FROM USER_INFO
WHERE JOINED LIKE '%2021%' AND AGE>=20 AND AGE <=29;
```
