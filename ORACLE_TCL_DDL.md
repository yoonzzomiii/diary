## 트랜잭션 제어와 세션

#### 트랜잭션이란?
- 더 이상 분할할 수 없는 최소 수행 단위

<br/>

#### TCL(Transaction Control Language)  
- 트랜잭션을 제어하기 위해 사용하는 명령어
- ROLLBACK : 트랜잭션을 취소하고 싶을 때
- COMMIT : 트랜잭션을 영원히 반영하고 싶을 때

```SQL
INSERT INTO DEPT_TCL VALUES(50, 'DATABASE', 'SEOUL');
UPDATE DEPT_TCL SET LOC = 'BUSAN' WHERE DEPTNO = 40;
DELETE FROM DEPT_TCL WHERE DNAME = 'RESEARCH';
SELECT *
    FROM DEPT_TCL;
    
ROLLBACK;
COMMIT;
```

<br/>

## 세션
- 데이터베이스 접속을 시작으로 접속을 종료하기까지 전체 기간
- 하나의 세션에는 여러 개의 트랜잭션 존재

#### 읽기 일관성
- 특성 세션에서 수행하는 데이터의 변경이 확정되기 전까지, 다른 세션에서는 본래의 데이터를 보여줌

<br/> <br/> 

***
## DDL : 객체를 생성, 변경, 삭제하는 '데이터 정의어'
- 객체에 관한 SQL문
1. CREATE : 테이블 생성성
2. ALTER : 테이블 내 칼럼 변경
3. RENAME : 테이블의 이름 변경
4. TRUNCATE : 테이블의 전체 데이터 삭제
5. DROP : 테이블과 저장된 모든 데이터 삭제

```

<br/>

#### CREATE : 테이블을 생성

```SQL
CREATE TAVBLE EMP_DDL(
    EMPNO    NUMBER(4),    --4자리 정수형 숫자
    ENAME    VARCHAR2(10), --가변 길이 문자열
    JOB      VARCHAR2(9),
    MGR      NUMBER(4),
    HIREDATE DATE,
    SAL      NUMBER(7, 2)  --소수 둘째자리까지 표현하는 7자리 숫자
    COMM     NUMBER(7, 제
```

===========
12강 연습문제

CREATE TABLE EMP_HW (
    EMPNO  NUMBER(4),
    ENAME  VARCHAR2(10),
    JOB    VARCHAR2(9),
    MGR    NUMBER(4),
    HIREDATE  DATE,
    SAL    NUMBER(7,2),
    COMM   NUMBER(7,2),
    DEPTNO NUMBER(2)
    );

DESC  EMP_HW;

==== 2   
ALTER TABLE EMP_HW
    ADD BIGO VARCHAR2(20);

DESC  EMP_HW;
    
    
====3    
ALTER TABLE EMP_HW
    MODIFY BIGO  VARCHAR2(30);
 
DESC  EMP_HW;


====4
ALTER TABLE EMP_HW
    RENAME COLUMN BIGO TO REMARK;

DESC  EMP_HW;


====5
INSERT INTO EMP_HW 
SELECT EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO, NULL 
  FROM EMP;
  
SELECT * FROM EMP_HW;

====6
DROP TABLE EMP_HW;


===========13강
SELECT * FROM DICT
WHERE TABLE_NAME LIKE '%TAB%';

SELECT * FROM ALL_TABLES
WHERE TABLE_NAME = 'EMP';

SELECT * FROM USER_TABLES
WHERE TABLE_NAME = 'EMP';


=============

