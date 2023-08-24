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
  가 수당을 받는 사원 수와 받지 않는 사원 수를 출력하세요.
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
