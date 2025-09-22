## 여러 기준으로 정렬하기

```sql
SELECT animal_id, name, datetime
FROM animal_ins
ORDER BY name ASC, datetime DESC;
```
- 이름은 오름차순 (정렬의 기본은 오름차순이기 때문에 ASC는 쓰지 않아도 무방), datetime은 내림차순으로 정렬


## 가장 비싼 상품 구하기

```sql
SELECT MAX(price) AS MAX_PRICE
FROM product;
```
- 집계함수 사용 - SELECT 할 때 구하고 싶은 함수(attribute) 입력하고 출력하고자 하는 속성값 이름으로 정의

## 흉부외과 또는 일반외과 의사 목록 출력하기

```sql
SELECT DR_NAME, DR_ID, MCDP_CD, DATE_FORMAT(HIRE_YMD, '%Y-%m-%d') AS HIRE_YMD
FROM doctor
WHERE mcdp_cd = "CS" OR mcdp_cd = "GS"
ORDER BY hire_ymd DESC, dr_name ASC;
```

- 시간 관련 내용 출력할 때 형식 지정하는 방법: DATE_FORMAT 함수 사용
> DATE_FORMAT(HIRE_YMD, '%Y-%m-%d') AS HIRE_YMD

- 조건식 작성: AND, OR과 같이 표현 & "is equl to"는 "="으로 표현
> MCDP_CD = "CS" OR MCDP_CD = "GS"

## 상위 n개 레코드
(mysql 기준)

```sql
SELECT NAME
FROM ANIMAL_INS
ORDER BY DATETIME
LIMIT 1;
```

- LIMIT: 정렬된 결과에서 원하는 개수만큼 행을 가져오는 데 사용

<참고>

(Oracle: 서브 쿼리에서 정렬 후 WHERE에서 rownum으로 원하는 개수 입력)
```sql
SELECT *
FROM (
    SELECT *
    FROM your_table
    ORDER BY column_name DESC
)
WHERE ROWNUM = 1;
```

(SQL Server, MS Access: TOP 사용)
```sql
SELECT TOP 1 *
FROM your_table
ORDER BY column_name DESC; -- 원하는 기준 컬럼으로 정렬
```

### 12세 이하인 여자 환자 목록 출력하기

```sql
SELECT PT_NAME, PT_NO, GEND_CD, AGE, IF(TLNO is NULL, 'NONE', TLNO) AS TLNO
FROM PATIENT
WHERE AGE <= 12 AND GEND_CD = "W"
ORDER BY AGE DESC, PT_NAME;
```

- IF문 활용: IF(조건문, 조건문이 TRUE인 경우, 조건문이 FALSE인 경우)

### 평균 일일 대여 요금

```sql
SELECT ROUND(AVG(DAILY_FEE), 0) AS AVERAGE_FEE
FROM CAR_RENTAL_COMPANY_CAR
WHERE CAR_TYPE = "SUV"
GROUP BY CAR_TYPE;
```

- ROUND(반올림하고자 하는 수, 자릿수): 소수점 첫번째 자리에서 반올림하면 소수점이 나타나지 않으므로 0을 입력

## 과일로 만든 아이스크림 고르기

```sql
SELECT FIRST_HALF.FLAVOR
FROM FIRST_HALF JOIN ICECREAM_INFO ON FIRST_HALF.FLAVOR = ICECREAM_INFO.FLAVOR
WHERE TOTAL_ORDER > 3000 AND INGREDIENT_TYPE = "fruit_based";
```

- JOIN하기: 두 개의 TABLE에 같은 attribute가 있으면 그 속성을 기준으로 두 테이블을 JOIN 해서 조건에 맞는 row를 찾음
> 테이블1 **JOIN** 테이블2 **ON** 테이블1.att **(조건)** 테이블2.att
