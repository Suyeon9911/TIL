## 프로그래머스 SQL 고득점 KIT


1. 과일로 만든 아이스크림 고르기 

https://school.programmers.co.kr/learn/courses/30/lessons/133025

- JOIN 사용
```MySQL
SELECT A.FLAVOR 
FROM FIRST_HALF AS A JOIN ICECREAM_INFO AS B
ON A.FLAVOR = B.FLAVOR
WHERE A.TOTAL_ORDER > 3000 AND B.INGREDIENT_TYPE = "fruit_based"
ORDER BY TOTAL_ORDER DESC
```

2. 12세 이하인 여자 환자 목록 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/132201

- 값이 비어있을 때 대체하기 ifnull
- 정렬조건 이중으로 설정


```MySQL

SELECT PT_NAME, PT_NO, GEND_CD, AGE, ifnull(TLNO, 'NONE')
FROM PATIENT
WHERE GEND_CD = "W" AND AGE <= 12
ORDER BY AGE DESC, PT_NAME ASC

```

3. 흉부외과 또는 일반외과 의사 목록 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/132203

- 날짜 포맷 출력 조건이랑 동일하게 맞춰주기 

```MySQL

SELECT DR_NAME, DR_ID, MCDP_CD, DATE_FORMAT(HIRE_YMD, '%Y-%m-%d') AS HIRE_YMD
FROM DOCTOR
WHERE MCDP_CD = 'CS' OR MCDP_CD = 'GS'
ORDER BY HIRE_YMD DESC, DR_NAME ASC

```


4. 3월에 태어난 여성 회원 목록 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/131120

- 날짜에서 month 만 출력하기 
- YEAR(기준날짜), MONTH(기준날짜), DAY(기준날짜) 
- HOUR(), MINUTE(), SECOND() 도 적용가능 

```MySQL

SELECT MEMBER_ID, MEMBER_NAME, GENDER, DATE_FORMAT(DATE_OF_BIRTH, "%Y-%m-%d")
FROM MEMBER_PROFILE
WHERE MONTH(DATE_OF_BIRTH) = 3 AND GENDER = 'W' AND TLNO IS NOT NULL
ORDER BY MEMBER_ID
```


5. 강원도에 위치한 생산공장 목록 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/131112

- 문자로 조건 걸기 LIKE 

```MySQL

SELECT FACTORY_ID, FACTORY_NAME, ADDRESS
FROM FOOD_FACTORY
WHERE ADDRESS LIKE "강원도%"
ORDER BY FACTORY_ID ASC

```


5. 서울에 위치한 식당 목록 출력하기

https://school.programmers.co.kr/learn/courses/30/lessons/131118

- <img width="493" alt="image" src="https://user-images.githubusercontent.com/81313960/198549094-a8273e58-ab65-477b-b321-a56bbef95ac6.png">



```MySQL
SELECT INFO.REST_ID,INFO.REST_NAME,
INFO.FOOD_TYPE, INFO.FAVORITES, INFO.ADDRESS, 
ROUND(AVG(REVIEW.REVIEW_SCORE),2) AS SCORE
FROM REST_REVIEW AS REVIEW INNER JOIN REST_INFO AS INFO
ON REVIEW.REST_ID = INFO.REST_ID
GROUP BY REVIEW.REST_ID
HAVING INFO.ADDRESS LIKE "서울%"
ORDER BY SCORE DESC, INFO.FAVORITES DESC

```
