# oracle start

## Oracle download

**otn.oracle.com**

## Oracle database connection

: sqlplus sys/oracle as sysdba

sys : user name oracle : password as sysdba : administrator connection sqlplus : SQL plus 쓴다

## Current user

현재 유저 보기 \(show current user\) : show user

## Table creation example

[http://cafe.daum.net/oracleoracle/SRAm/1](http://cafe.daum.net/oracleoracle/SRAm/1)

alter session set nls\_Date\_format='RR/MM/DD'; drop table emp; drop table dept;

CREATE TABLE DEPT \(DEPTNO number\(10\), DNAME VARCHAR2\(14\), LOC VARCHAR2\(13\) \);

INSERT INTO DEPT VALUES \(10, 'ACCOUNTING', 'NEW YORK'\); INSERT INTO DEPT VALUES \(20, 'RESEARCH', 'DALLAS'\); INSERT INTO DEPT VALUES \(30, 'SALES', 'CHICAGO'\); INSERT INTO DEPT VALUES \(40, 'OPERATIONS', 'BOSTON'\);

CREATE TABLE EMP \( EMPNO NUMBER\(4\) NOT NULL, ENAME VARCHAR2\(10\), JOB VARCHAR2\(9\), MGR NUMBER\(4\) , HIREDATE DATE, SAL NUMBER\(7,2\), COMM NUMBER\(7,2\), DEPTNO NUMBER\(2\) \);

INSERT INTO EMP VALUES \(7839,'KING','PRESIDENT',NULL,'81-11-17',5000,NULL,10\); INSERT INTO EMP VALUES \(7698,'BLAKE','MANAGER',7839,'81-05-01',2850,NULL,30\); INSERT INTO EMP VALUES \(7782,'CLARK','MANAGER',7839,'81-05-09',2450,NULL,10\); INSERT INTO EMP VALUES \(7566,'JONES','MANAGER',7839,'81-04-01',2975,NULL,20\); INSERT INTO EMP VALUES \(7654,'MARTIN','SALESMAN',7698,'81-09-10',1250,1400,30\); INSERT INTO EMP VALUES \(7499,'ALLEN','SALESMAN',7698,'81-02-11',1600,300,30\); INSERT INTO EMP VALUES \(7844,'TURNER','SALESMAN',7698,'81-08-21',1500,0,30\); INSERT INTO EMP VALUES \(7900,'JAMES','CLERK',7698,'81-12-11',950,NULL,30\); INSERT INTO EMP VALUES \(7521,'WARD','SALESMAN',7698,'81-02-23',1250,500,30\); INSERT INTO EMP VALUES \(7902,'FORD','ANALYST',7566,'81-12-11',3000,NULL,20\); INSERT INTO EMP VALUES \(7369,'SMITH','CLERK',7902,'80-12-09',800,NULL,20\); INSERT INTO EMP VALUES \(7788,'SCOTT','ANALYST',7566,'82-12-22',3000,NULL,20\); INSERT INTO EMP VALUES \(7876,'ADAMS','CLERK',7788,'83-01-15',1100,NULL,20\); INSERT INTO EMP VALUES \(7934,'MILLER','CLERK',7782,'82-01-11',1300,NULL,10\);

commit;

## Query example

sql&gt; select ename, sal from emp; 쿼리 명령어들

## Column information

sql&gt; desc emp desc: describe 의 약자

EMPNO : 사원번호 ENAME : 사원이름 JOB : 직업 MGR : 관리자의 사원번호 HIREDATE: 입사일 SAL : 월급 COMM : 커미션 DEPTNO : 부서번호

Pb 1. print out name and salaries Pb 1. 사원이름, 월급, 직업을 출력하시오

select ename, sal, job

from emp;

문제 2. 사원번호, 이름, 월급, 부서번호를 출력하시오

select empno, ename, sal, deptno from emp;

문제 3. 사원이름, 입사일, 월급, 커미션, 관리자 번호 출력하시오

select ename, hiredate, sal, comm, mgr from emp;

문제 4. 이름과 입사일을 출력하는데 최근에 입사한 사원부터 출력하시오

select ename, hiredate from emp order by sal desc;

## 한페이지에 나오는 크기 변경

set pages 400

## order by 절

“데이터 정렬하는 절”

ex\) select ename, sal from emp order by sal asc;

낮은값에서 높은값순으로 정렬

옵션: 1. asc → 낮은값에서 높은값 2. desc → 높은값에서 낮은값 순으로 정렬

## 컬럼과 로우 설명

테이블은 데이터를 저장하는 논리적 저장소 이고 컬럼\(columns\)과 로우\(row\)로 구성되어 있다

![](https://d2mxuefqeaa7sj.cloudfront.net/s_6855E21501F96623D34B58A505635A34938CC8DC4F80CD2F9115D3A79682036F_1522113587258_image.png)

dept 테이블로 확인 select \* from dept;

select empno. ename, job, sal, comm from emp; 실행순서 : from → select

모든컬럼조회 select \* from emp;

## 예쁘게 테이블을 출력하는 방법

SQL&gt; show lines ← 테이블 결과 출력 가로 사이즈 SQL&gt; set lines 300 SQL&gt; set pages 400

## 중복 데이터를 제거하는 키워드

select distinct job from emp;

## SQL GATE 설치

install in cmd by administrator

select \* from emp; \(ctrl + enter\)

문제6. 부서번호 중복제거 출력 select distinct deptno f rom emp;

## 연결연산자

→ \|\| ex\) select ename \|\| ‘의 직업은’ \|\| job from emp; **\(그대로 복사x\)**

문제 7. SCOTT 의 부서번호는 10번 입니다. 라고 결과가 출력되게 하시오 select ename \|\| '의 부서번호는' \|\| deptno \|\| '입니다' from emp;

문제 8. 아래와 같이 결과가 출력되게 하시오! select ename \|\| '의 월급은 ' \|\| sal \|\| '입니다' from emp order by sal desc;

컬럼별칭 사용법 select ename as “이름”, sal as “월급” from emp;

문제 9. 이름과 연봉\(sal_12\) 을 출력하는데 연봉이 높은 사원부터 출력하고 컬럼명을 한글로 이름, 연봉으로 출력 select ename as “이름”, sal_12 as "연봉" from emp order by sal\(or 연봉\) desc; 실행순서\) from → select → order , Therefore you can refer 연봉 in the order phase

문제10. 이름, 월급, 직업을 출력하는데 직업을 ABCD 순으로 출력되게 하고 컬럼명을 한글로 이름, 월급, 직업으로 출력되게 하시오 select ename as "이름", sal as "월급", job as "직업" from emp order by job asc;

문제 11. \(점심시간 문제\) 라인검사

아래와 같이 출력하는데 최근에 입사한 사원부터 출력되게 하시오 select ename \|\| '의 입사일은' \|\| hiredate \|\| '입니다' as "사원정보" from emp order by hiredate desc;

## Null 값의 의미?

1. 데이터가 없는 상태
2. 알수 없는 값 \(unknown\)

예제 \) select ename,sal, comm from emp;

select ename, sal, comm, sal+comm from emp;

왜 null을 만들었나? null이 존재하면 그룹함수를 사용할때 연산이 빨라지는 장점이 있다.

예\) select sum\(comm\) from emp; select sum\(nvl\(comm,0\)\) from emp;

문제12. 이름, 월급, 커미션을 출력하는데 커미션이 null인 사원들은 0으로 출력되게 하시오! select ename, sal, nvl\(comm,0\)

from emp;

## NVL Function\(null value logic\)

Null value logic ex\) nvl\(column, 0\) : null 대신에 0을 출력

문제13. 이름,월급,커미션, 월급+ 커미션을 출력하는데 요번달 월급을 줄수 있도록 결과가 출력되게 하시오! select ename, sal, comm , sal+nvl\(comm,0\)

from emp;

## 연산자의 종류 3가지

* 산술 연산자 : \*/ + -
* 비교 연산자 : &gt;, &lt;, &gt;=, &lt;=, =, &lt;&gt;, !=, ^= \(같지 않다 3가지\)
* 논리 연산자:  and, or, not

