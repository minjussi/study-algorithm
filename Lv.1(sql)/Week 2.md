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
