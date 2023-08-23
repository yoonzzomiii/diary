## SELECT문 알아보기

'''SQL
DESC EMP;

select *
    from emp;
    
SELECT EMPNO, ENAME, DNO
    FROM EMP;
    
SELECT DISTINCT DNO
    FROM EMP;
'''


SELECT DISTINCT DNO
    FROM EMP
    ORDER BY DNO;   --ORDER BY : 정렬, 기본 오름차순
    
SELECT DISTINCT DNO
    FROM EMP
    ORDER BY DNO DESC;   --ORDER BY DESC: 내림차순 정렬
    
SELECT DISTINCT DNO, JOB
    FROM EMP
    ORDER BY DNO;   --DNO 기준으로 정렬
    
SELECT DISTINCT DNO, JOB
    FROM EMP
    ORDER BY DNO, JOB;  --DNO(먼저) 이후 JOB 기준으로 정렬
    
SELECT DISTINCT DNO, JOB
    FROM EMP
    ORDER BY DNO DESC, JOB ASC;    --DNO는 내림차순, JOB은 오름차순으로
    
SELECT DNO "부서번호", JOB "업무"   --앨리어스(별칭) 부여
    FROM EMP;

SELECT DNO AS 부서번호, JOB AS 업무   --앨리어스(별칭) 부여
    FROM EMP;

SELECT EMPLOYEE.DNO "부서번호", JOB "업무"   --테이블 앨리어스 안 붙여도 출력됨
    FROM EMP EMPLOYEE;    --테이블에 앨리어스 부여
 
 --테이블 두 개
SELECT EMPLOYEE.DNO AS 부서번호, EMPLOYEE.JOB AS 업무, DEPARTMENT.DNAME   --테이블 앨리어스 안 붙여도 출력됨
    FROM EMP EMPLOYEE, DEPT DEPARTMENT
    ORDER BY DDAME;    
    

    
SELECT EMPLOYEE.ENAME, EMPLOYEE.EMPNO, EMPLOYEE.DNO AS "부서번호", EMPLOYEE.JOB AS "업무", DEPARTMENT.DNAME -- 해당 TITLE을 지정하여 보고싶을 때, 엘리어스를 지정
  FROM EMP EMPLOYEE, DEPT DEPARTMENT
  WHERE EMPLOYEE.DNO = DEPARTMENT.DEPTNO --값이 같은 것만
  ORDER BY EMPLOYEE.ENAME;
  
SELECT *
  FROM EMP EMPLOYEE, DEPT DEPARTMENT
  WHERE EMPLOYEE.DNO = DEPARTMENT.DEPTNO --값이 같은 것만
  ORDER BY EMPLOYEE.ENAME;
  
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
    
    
    
    
    ==================================
    
alter table emp rename column dno to deptno; --컬럼을 RENAME한다
    
SELECT *
    FROM EMP;

select *
    from emp
    where dno = 30;
    
select *
    from emp
    where dno = 30
    and job = 'SALESMAN';    --
    
    
==============
!!!!!!연습문제!!!!!!
-- 5강 1번
-- EMP 테이블을 사용하여 다음과 같이 사원 이름(ENAME)이 S로 끝나는 사원 데이터를 모두 출력하는 SQL문을 작성해 보세요.

SELECT *
    FROM EMP
    WHERE ENAME LIKE '%S';
    
 
--5강 2번    
-- EMP 테이블을 사용하여 30번 부서(DEPTNO)에서 근무하고 있는 사원 중에 
-- 직책(JOB)이 SALESMAN인 사원의 사원 번호, 이름, 직책, 급여, 부서 번호를 출력하는 SQL문을 작성해 보세요.

SELECT EMPNO, ENAME, JOB, SAL, DNO
    FROM EMP;

SELECT EMPNO, ENAME, JOB, SAL, DNO
    FROM EMP
    WHERE DNO = 30
    AND JOB = 'SALESMAN';
  
    
--- 5강 3번
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
    
    
----5강 4번
SELECT *
    FROM EMP
    MINUS
SELECT*
    FROM EMP
    WHERE SAL >= 2000
        AND SAL <= 3000;


----5강 5번
SELECT ENAME, EMPNO, SAL, DNO
    FROM EMP
    WHERE ENAME LIKE '%E%'
    AND DNO = 30
INTERSECT
SELECT ENAME, EMPNO, SAL, DNO
    FROM EMP
    WHERE SAL < 1000
    OR SAL > 2000;
    
    
----5강 6번
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
    
============================

===========6장==============
select * from emp
    where job = 'PRESIDENT';
    
select * from emp
    WHERE ENAME = '홍길동';

select ENAME, LENGTH(ENAME)
    from emp
   WHERE ENAME = '홍길동';
   
SELECT EMPNO, ENAME, LENGTH(ENAME)
    FROM EMP
    WHERE ENAME = '홍길동';

SELECT EMPNO, ENAME, LENGTH(ENAME), JOB
    FROM EMP
    WHERE JOB = 'CLERK';   --SPACE도 LENGTH로 카운트 됨
    
SELECT EMPNO, ENAME, LENGTH(ENAME), LENGTH(REPLACE(ENAME, ' ', ''))
    FROM EMP
    WHERE JOB = 'CLERK'; --SPACE는 많이 써도 하나로 카운트 됨

    
SELECT SYSDATE -30  --SYSDATE : 현재 날짜와 시간
    FROM DUAL;      --DUAL은 SYSDATE를 많이 사용함, DUAL은 데이터 이름

SELECT TO_CHAR(SYSDATE, 'YYYYMMDD') -1  --TO_CHAR 문자열로 바꿔주는 함수
    FROM DUAL;
    
SELECT JOB, REPLACE(JOB, 'CLERK', 'CL') --대체할 값 안 쓰면 NULL
    FROM EMP;

--ROUND 함수; 많이 쓰인다    
SELECT ROUND(SAL),
       ROUND(SAL, -2) AS SAL_2
    FROM EMP;
    
    
-SYSDATE
SELECT SYSDATE -60
    FROM DUAL;
