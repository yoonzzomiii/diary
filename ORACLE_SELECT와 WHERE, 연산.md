## SELECT문 알아보기

#### SELECT로 테이블 불러오기
```SQL
select *   
    from emp;   -- * 전체를 불러온다.
    
SELECT EMPNO, ENAME, DNO   --선택한 칼럼만 불러온다.
    FROM EMP;
```


#### DISTINCT : 중복된 값은 제외하고 출력
```SQL
SELECT DISTINCT DNO
    FROM EMP;

SELECT DISTINCT DNO
    FROM EMP
    ORDER BY DNO;   --ORDER BY : 정렬, 기본값은 오름차순 정렬
    
SELECT DISTINCT DNO
    FROM EMP
    ORDER BY DNO DESC;   --ORDER BY DESC: 내림차순 정렬
    
SELECT DISTINCT DNO, JOB
    FROM EMP
    ORDER BY DNO;   
    
SELECT DISTINCT DNO, JOB
    FROM EMP
    ORDER BY DNO, JOB;  --DNO(먼저) 이후 JOB 기준으로 정렬
    
SELECT DISTINCT DNO, JOB
    FROM EMP
    ORDER BY DNO DESC, JOB ASC;    --DNO는 내림차순, JOB은 오름차순으로
```


#### 앨리어스 사용하기
1. SELECT DNO "부서번호" - 따옴표 사용하기
2. SELECT DNO AS 부서번호 - AS를 이용하기(따옴표는 붙여도/붙이지 않아도 상관 없음)

```SQL
SELECT DNO "부서번호", JOB "업무"   --따옴표를 이용해 앨리어스(별칭) 부여
    FROM EMP;

SELECT DNO AS 부서번호, JOB AS 업무   --AS를 이용해 앨리어스(별칭) 부여
    FROM EMP;

SELECT EMPLOYEE.DNO "부서번호", EMPLOYEE.JOB "업무"   --테이블 앨리어스 안 붙여도 출력됨
    FROM EMP EMPLOYEE;    --테이블에 앨리어스 부여
 
 --테이블 두 개
SELECT EMPLOYEE.DNO AS 부서번호, EMPLOYEE.JOB AS 업무, DEPARTMENT.DNAME   --테이블 앨리어스 안 붙여도 출력됨
    FROM EMP EMPLOYEE, DEPT DEPARTMENT
    ORDER BY DDAME;    
```

```    
SELECT EMPLOYEE.ENAME, EMPLOYEE.EMPNO, EMPLOYEE.DNO AS "부서번호", EMPLOYEE.JOB AS "업무", DEPARTMENT.DNAME -- 해당 TITLE을 지정하여 보고싶을 때, 엘리어스를 지정
  FROM EMP EMPLOYEE, DEPT DEPARTMENT
  WHERE EMPLOYEE.DNO = DEPARTMENT.DEPTNO --값이 같은 것만
  ORDER BY EMPLOYEE.ENAME;
  
SELECT *
  FROM EMP EMPLOYEE, DEPT DEPARTMENT
  WHERE EMPLOYEE.DNO = DEPARTMENT.DEPTNO --값이 같은 것만
  ORDER BY EMPLOYEE.ENAME;
```

#### SELECT문 실습
```SQL
--연봉만 출력(SAL)
SELECT SAL 
    FROM EMP;
    
--사원과 연봉 출력(SAL)
SELECT ENAME, SAL*12 연봉    --SAL*12 칼럼에 연봉이라는 앨리어스를 부여함
    FROM EMP;
    
--사원과 연봉(월급+보너스), 보너스 출력(SAL)
SELECT ENAME, SAL*12 + COMM 연봉, COMM    --SAL*12 + COMM(보너스) 칼럼에 연봉이라는 앨리어스를 부여함
    FROM EMP;
    
SELECT ENAME, SAL*12 + COMM 연봉, COMM    --SAL*12 + COMM(보너스) 칼럼에 연봉이라는 앨리어스를 부여함
    FROM EMP                             --COMM이 NULL이면, NULL값 출력
    ORDER BY ENAME;
    
    
SELECT ENAME, SAL*12 + COMM 연봉, COMM    --SAL*12 + COMM(보너스) 칼럼에 연봉이라는 앨리어스를 부여함
    FROM EMP                             
    ORDER BY ENAME DESC, 연봉 ASC;
```
    
    

***
#### AND 연산자 
```SQL
alter table emp rename column dno to deptno; --컬럼을 RENAME한다
    
SELECT *
    FROM EMP;

select *
    from emp
    where dno = 30;
    
select *
    from emp
    where dno = 30
    and job = 'SALESMAN';    
```

***
### 연습문제

1. EMP 테이블을 사용하여 다음과 같이 사원 이름(ENAME)이 S로 끝나는 사원 데이터를 모두 출력하는 SQL문을 작성해 보세요.
```SQL
SELECT *
    FROM EMP
    WHERE ENAME LIKE '%S';
```


    
2. EMP 테이블을 사용하여 30번 부서(DEPTNO)에서 근무하고 있는 사원 중에 직책(JOB)이 SALESMAN인 사원의 사원 번호, 이름, 직책, 급여, 부서 번호를 출력하는 SQL문을 작성해 보세요.

```SQL
SELECT EMPNO, ENAME, JOB, SAL, DNO
    FROM EMP;

SELECT EMPNO, ENAME, JOB, SAL, DNO
    FROM EMP
    WHERE DNO = 30
    AND JOB = 'SALESMAN';
```

3. EMP 테이블을 사용하여 20번, 30번 부서에 근무하고 있는 사원 중 급여(SAL)가 2000 초과인 사원을 다음 두 가지 방식의 SELECT문을 사용하여 사원 번호, 이름, 급여, 부서 번호를 출력하는 SQL문을 자성해 보세요.
- 집합 연산자를 사용하지 않은 방식
- 집합 연산자를 사용한 방식
```SQL
SELECT EMPNO, ENAME, SAL, DNO
    FROM EMP
    WHERE SAL > 2000;
    
SELECT EMPNO, ENAME, SAL, DNO
    FROM EMP
    WHERE SAL > 2000
    UNION ALL
SELECT EMPNO, ENAME, SAL, DNO
    FROM EMP
    WHERE SAL > 2000;
``` 

4. NOT BETWEEN A AND B 연산자를 쓰지 않고, 급여(SAL) 열 값이 2000 이상 3000 이하 범위 이외의 값을 가진 데이터만 출력하도록 SQL문을 작성해 보세요.
```SQL
SELECT *
    FROM EMP
    MINUS
SELECT*
    FROM EMP
    WHERE SAL >= 2000
        AND SAL <= 3000;
```

5. 사원 이름에 E가 포함되어 있는 30번 부서의 사원 중 급여가 1000~2000 사이가 아닌 사원 이름, 사원 번호, 급여, 부서 번호를 출력하는 SQL문을 작성해 보세요.
```SQL
SELECT ENAME, EMPNO, SAL, DNO
    FROM EMP
    WHERE ENAME LIKE '%E%'
    AND DNO = 30
INTERSECT
SELECT ENAME, EMPNO, SAL, DNO
    FROM EMP
    WHERE SAL < 1000
    OR SAL > 2000;
```
    
6. 추가 수당이 존재하지 않고 상급자가 있고 직책이 MANAGER, CLERK인 사원 중에서 사원 이름의 두 번째 글자가 L이 아닌 사원의 정보를 출력하는 SQL문을 작성해 보세요.    
```SQL
SELECT *
    FROM EMP;

SELECT *
    FROM EMP
    WHERE COMM IS NULL
    AND MGR IS NOT NULL 
    AND JOB = 'MGR'
    OR JOB = 'CLERK'
MINUS
SELECT *
    FROM EMP
    WHERE ENAME LIKE '_L%';
```

