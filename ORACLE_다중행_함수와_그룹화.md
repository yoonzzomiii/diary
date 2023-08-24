## 7강. 다중행 함수와 데이터 그룹화

### 다중행 함수
- SUM(합계)
- COUNT(데이터 개수)
- MAX(최댓값)
- MIN(최솟값)
- AVG(평균값)

#### 하나의 열에 출력 결과를 담는 다중행 함수
```SQL
--SUM 함수를 사용해 급여 합계 출력하기
SELECT SUM(SAL)
    FROM EMP;

SELECT ENAME, SUM(SAL)
    FROM EMP:      -- 에러 : SUM(SAL)은 값이 하나인데, ENAME은 다수의 값이 출력됨
```

```SQL
--EMP 테이블의 데이터 개수 출력하기
SELECT CUNT(*)
    FROM EMP;

--부서 번호가 30번인 직원 수 구하기
SELECT COUNT(*)
    FROM EMP
    WHERE DEPTNO = 30;
```

***

#### GROUP BY : 결과 값을 원하는 열로 묶어 출력
```SQL
--부서 번호 및 직책별 평균 급여로 정렬하기
SELECT AVG(SAL), DEPTNO, JOB
    FROM EMP
    GROUP BY DEPTNO, JOB
    ORDER BY DEPTNO, JOB;
```

#### HAVING : GROUP BY절게 조건을 줄 때 사용
```SQL
SELECT DEPTNO, JOB, AVG(SAL)
    FROM EMP
    GROUP BY DEPTNO, JOB
        HAVING AVG(SAL) >= 2000
    ORDER BY DEPTNO, JOB;

--WHERE절과 HAVING절의 사용에 유의
SELECT DEPTNO, JOB, AVG(SAL)
    FROM EMP
    WHERE SAL <= 3000
    GROUP BY DEPTNO, JOB
        HAVING AVG(SAL) >= 2000
    ORDER BY DEPTNO, JOB;
```

***

#### 그룹화 함수 : ROLLUP, CUBE, GROUPING SETS 

- ROLLUP : 소계, 총계
- CUBE : 소계, 총계, 데이터별 합

***
***

### 7강 연습문제

1. EMP 테이블을 이용해 부서 번호, 평균 굽여, 최고 급여, 최저 급여, 사원 수를 출력합니다. 단 평균 급여를 출력할 때 소수점을 제외하고 각 부서 번호 별로 출력하세요.
```SQL
SELECT DNO, TRUNC(AVG(SAL)) AS AVG_SAL, MAX(SAL) AS MAX_SAL, MIN(SAL) AS MIN_SAL, COUNT(ENAME) AS CNT
    FROM EMP
    GROUP BY DNO;
```

2. 같은 직책에 종사하는 사원이 3명 이상인 직책과 인원 수를 출력하세요.
```SQL
SELECT JOB , COUNT(*)
    FROM EMP
    GROUP BY JOB
        HAVING COUNT(*) >= 3;
```

3. 사원들의 입사 연도를 기준으로 부서별로 몇 명이 입사했는지 출력하세요.
```SQL
SELECT TO_CHAR(HIREDATE,'YYYY'), DNO, COUNT(ENAME)
    FROM EMP
    GROUP BY TO_CHAR(HIREDATE,'YYYY'), DNO
    ORDER BY TO_CHAR(HIREDATE,'YYYY');
```

4. 추사 수당을 받는 사원 수와 받지 않는 사원 수를 출력하세요.
```SQL
SELECT COUNT(ENAME),
    NVL2(COMM, 'O', 'X') AS EXIST_COMM
    FROM EMP
    GROUP BY NVL2(COMM, 'O', 'X');
```

5. 각 부서의 입사 연도별 사원 수, 최고 급여, 급여 합, 평균 급여를 출력하고 각 부서별 소계와 총계를 출력하세요.
```SQL
SELECT DNO, TO_CHAR(HIREDATE, 'YYYY'), COUNT(ENAME), MAX(SAL), SUM(SAL), AVG(SAL)
    FROM EMP
    GROUP BY ROLLUP (DNO, TO_CHAR(HIREDATE, 'YYYY'));
```    
