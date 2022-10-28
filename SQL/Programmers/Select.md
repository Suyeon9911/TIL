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

