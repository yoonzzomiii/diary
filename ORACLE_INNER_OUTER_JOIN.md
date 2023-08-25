## JOIN : 테이블 간 동일 칼럼의 데이터를 묶어서, 테이블을 연결!!
  
- 조인의 특징 : 테이블의 별칭 설정이 가능
```SQL
SELECT *
	FROM EMP E, DEPT D
    WHERE E.DEPTNO = D.DEPTNO
    ORDER BY EMPNO;
``` 

 

### 조인의 종류   
1. 등가 조인( INNER JOIN)  : '=' 사용
- 열 이름에 각각의 테이블 이름도 함께 명시
```SQL
SELECT E.EMPNO, E.NAME, D.DEPTNO, D.NAME, D.LOC
	FROM EMP E, DEPT D
    WHERE E.DEPTNO = D.DEPTNO  --EMP와 DEPT테이블의 DEPTNO 칼럼이 동일한 값
    ORDER BY D.DEPTNO, E.EMPNO;
```
***    
2. 자체 조인 :  하나의 테이블을 여러 테이블처럼 사용
- 같은 테이블을 두 번 사용하여 자체 조인하기
```SQL
SELECT 	E1.EMPNO, E1.ENAME, E1.MGR,
		E2.EMPNO AS MNG_ENOMP,
    	E2.ENAME AS MNG_ENAME
    FROM EMP E1, EMP E2      --EMP 테이블을 두 번 사용함
    WHERE E1.MGR = E2.EMPNO;
```
***  
3. 외부 조인(OUTER JOIN)
- LEFT / RIGHT 기준으로 데이터를 출력함. 상대 테이블에 데이터가 없어도 NULL 값을 부여해 출력!
   
#### LEFT OUTER JOIN
```SQL
SELECT DISTINCT EMP.DEPTNO, DEPT.DEPTNO   --중복없이
    FROM EMP, DEPT
    WHERE EMP.DEPTNO = DEPT.DEPTNO(+)  --LEFT OUTER JOIN
    ORDER BY EMP.DEPTNO;
```     

#### RIGHT OUTER JOIN   
```SQL
SELECT DISTINCT EMP.DEPTNO, DEPT.DEPTNO   --중복없이
    FROM EMP, DEPT
    WHERE EMP.DEPTNO(+) = DEPT.DEPTNO   --RIGHT OUTER JOIN
    ORDER BY EMP.DEPTNO;
```   
***   
### OUTER / INNER JOIN 작성 방법
- WHERE 절 이외에, FROM 절에 LEFT/RIGHT/FULL JOIN, INNER JOIN을 작성하여 실행이 가능하다.
- WHERE 절에 작성하는 방법은 (+)의 위치가 헷갈릴 수도 있으니, 후자의 방법이 명시적이고 더욱 깔끔하다 생각함

1. LEFT OUTER JOIN 예시
```SQL
SELECT DISTINCT EMP.DEPTNO, DEPT.DEPTNO   --중복없이
    FROM EMP LEFT OUTER JOIN DEPT   --왼쪽 기준!
        ON EMP.DEPTNO = DEPT.DEPTNO
    ORDER BY EMP.DEPTNO;
 ```

2. RIGHT OUTER JOIN 예시
```SQL
SELECT DISTINCT EMP.DEPTNO, DEPT.DEPTNO   --중복없이
    FROM EMP RIGHT OUTER JOIN DEPT   --오른쪽 기준!
        ON EMP.DEPTNO = DEPT.DEPTNO
    ORDER BY EMP.DEPTNO;
 ```

3.FULL OUTER JOIN 예시
```SQL
SELECT DISTINCT EMP.DEPTNO, DEPT.DEPTNO   --중복없이
    FROM EMP FULL OUTER JOIN DEPT   --양쪽 다
        ON EMP.DEPTNO = DEPT.DEPTNO
    ORDER BY EMP.DEPTNO;
```
 

4. INNER JOIN 예시
```SQL
SELECT DISTINCT EMP.DEPTNO, DEPT.DEPTNO   --중복없이
    FROM EMP INNER JOIN DEPT   --INNER JOIN(등가조인)
           ON EMP.DEPTNO = DEPT.DEPTNO
    ORDER BY EMP.DEPTNO;
```

