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
1. CREATE : 테이블 생성
2. ALTER : 테이블 내 칼럼 변경
3. RENAME : 테이블의 이름 변경
4. TRUNCATE : 테이블의 전체 데이터 삭제
5. DROP : 테이블과 저장된 모든 데이터 삭제


<br/>

### 1. CREATE : 테이블 생성

```SQL
CREATE TAVBLE EMP_DDL(
    EMPNO    NUMBER(4),    --4자리 정수형 숫자
    ENAME    VARCHAR2(10), --가변 길이 문자열
    JOB      VARCHAR2(9),
    MGR      NUMBER(4),
    HIREDATE DATE,
    SAL      NUMBER(7, 2)  --소수 둘째자리까지 표현하는 7자리 숫자
    COMM     NUMBER(7, 2)
);
```
#### 기존 테이블 열 구조와 데이터를 복사하여 새 테이블 생성하기
```SQL
--다른 테이블을 복사하여 테이블 생성
CREATE TABLE DEPT_DDL
    AS SELECT * FROM DEPT;

--다른 테이블의 일부를 복사하여 테이블 생성
CREATE TABLE EMP_DDL_30
    AS SELECT *
        FROM EMP
        WHERE DEPTNO = 30;

--기존 테이블의 열 구조만 복사하여 생성
--조건식이 항상 FALSE인 WHERE절 사용
CREATE TABLE EMPDEPT_DDL
    AS SELECT E.EMPNO, E.ENAME, E.JOB, E.MGR, E.HIREDATE, E.SAL
                E.COMM, D.DEPTNO, D.DNAME, D.LOC
        FROM EMP E, DEPT D
        WHERE 1 <> 1;  --FALSE >> 데이터 없이, 열 구조만 같은 빈 테이블 생성
```

#### 2. ALTER : 테이블의 열 변경
- ADD : 테이블에 열 추가
```SQL
ALTER TABLE EMP_ALTER
    ADD HP VARCHAR2(20);   --HP열 추가
```

- RENAME : 테이블의 열 이름 변경
```SQL
ALTER TALE EMP_ALTER
    RENAME COLUMN HP TO TEL;   --HP열의 이름을 TEL로 변경
```

- MODIFY : 테이블의 열 자료형 변경
```SQL
ALTER TABLE EMP_ALTER
    MODIFY EMPNO NUMBER(5);
```

- DROP : 테이블의 특정 열을 삭제
```SQL
ALTER TABLE EMP_ALTER
    DROP COLMN TEL;     --TEL 열 삭제
```

<BR/>
#### 3. RENAME : 테이블의 이름 변경
- 변경 후 본래의 테이블 이름은 사용 불가
```SQL
RENAME EMP_ALTER TO EMP_RENAME;
```

<BR/>
#### 4. TRUNCATE : 테이블의 데이터를 삭제
- 테이블의 전체 데이터 삭제
- DDL문, ROLLBACK 불가
- DELETE문으로도 수행 가능 >> ROLLBACK 가능
```SQL
TRUNCATE TABLE EMP_RENAME;
```

<BR/>
#### 5. DROP : 테이블과 저장된 데이터 모두 삭제
- 데이터 뿐만 아니라 테이블까지 삭제
```SQL
DROP TABLE EMP_RENAME;
```

