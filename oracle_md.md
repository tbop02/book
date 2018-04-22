---
author: Windows 사용자
title: Oracle
---

Oracle

2018[년 ]{.s3}4[월 ]{.s3}4[일 수요일 오후 ]{.s3}2:07

\

[Chapter 1. introduction]{#bookmark0}

\

[Oracle download]{#bookmark1}

-   otn.oracle.com

    \

    [Oracle database connection]{#bookmark2}

    : sqlplus sys/oracle as sysdba sys : user name

    oracle : password

    as sysdba : administrator connection sqlplus : SQL plus 쓴다

    \

    [Current user]{#bookmark3}

    현재 유저 보기 (show current user)

    : show user

    \

    [Table creation]{#bookmark4}[example]{.s5}

    <http://cafe.daum.net/oracleoracle/SRAm/1>

    alter session set nls\_Date\_format='RR/MM/DD'; drop table emp;

    drop table dept; CREATE TABLE DEPT

    (DEPTNO number(10),

    DNAME VARCHAR2(14), LOC VARCHAR2(13) );

    INSERT INTO DEPT VALUES (10, 'ACCOUNTING', 'NEW YORK'); INSERT INTO
    DEPT VALUES (20, 'RESEARCH', 'DALLAS');

    INSERT INTO DEPT VALUES (30, 'SALES', 'CHICAGO'); INSERT INTO DEPT
    VALUES (40, 'OPERATIONS', 'BOSTON');

    CREATE TABLE EMP (

    EMPNO NUMBER(4) NOT NULL,

    ENAME VARCHAR2(10),

    \

    JOB VARCHAR2(9),

    MGR NUMBER(4) ,

    HIREDATE DATE,

    SAL NUMBER(7,2), COMM NUMBER(7,2),

    DEPTNO NUMBER(2) );

    INSERT INTO EMP VALUES
    (7839,'KING','PRESIDENT',NULL,'81-11-17',5000,NULL,10); INSERT INTO
    EMP VALUES (7698,'BLAKE','MANAGER',7839,'81-05-01',2850,NULL,30);
    INSERT INTO EMP VALUES
    (7782,'CLARK','MANAGER',7839,'81-05-09',2450,NULL,10); INSERT INTO
    EMP VALUES (7566,'JONES','MANAGER',7839,'81-04-01',2975,NULL,20);
    INSERT INTO EMP VALUES (7654,'MARTIN','SALESMAN',7698,'81-09-
    10',1250,1400,30);

    INSERT INTO EMP VALUES
    (7499,'ALLEN','SALESMAN',7698,'81-02-11',1600,300,30); INSERT INTO
    EMP VALUES (7844,'TURNER','SALESMAN',7698,'81-08-21',1500,0,30);
    INSERT INTO EMP VALUES
    (7900,'JAMES','CLERK',7698,'81-12-11',950,NULL,30); INSERT INTO EMP
    VALUES (7521,'WARD','SALESMAN',7698,'81-02-23',1250,500,30); INSERT
    INTO EMP VALUES
    (7902,'FORD','ANALYST',7566,'81-12-11',3000,NULL,20); INSERT INTO
    EMP VALUES (7369,'SMITH','CLERK',7902,'80-12-09',800,NULL,20);
    INSERT INTO EMP VALUES
    (7788,'SCOTT','ANALYST',7566,'82-12-22',3000,NULL,20); INSERT INTO
    EMP VALUES (7876,'ADAMS','CLERK',7788,'83-01-15',1100,NULL,20);
    INSERT INTO EMP VALUES
    (7934,'MILLER','CLERK',7782,'82-01-11',1300,NULL,10);

    commit;

    \

    [Query example]{#bookmark5}

    sql&gt; select ename, sal from emp;

    쿼리 명령어들

    \

    [Column information]{#bookmark6}

    sql&gt; desc emp

    desc: describe 의 약자 EMPNO : 사원번호 ENAME : 사원이름 JOB : 직업

    MGR : 관리자의 사원번호 HIREDATE: 입사일

    SAL : 월급

    \

    COMM : 커미션

    DEPTNO : 부서번호

    \

    Pb 1. print out name and salaries select ename, sal, job

    from emp;

    문제 2. 사원번호, 이름, 월급, 부서번호를 출력하시오 select empno,
    ename, sal, deptno

    from emp;

    \

    문제 3. 사원이름, 입사일, 월급, 커미션, 관리자 번호 출력하시오
    select ename, hiredate, sal, comm, mgr

    from emp;

    문제 4. 이름과 입사일을 출력하는데 최근에 입사한 사원부터 출력하시오
    select ename, hiredate

    from emp

    order by sal desc;

    \

    [Set pages]{#bookmark7}

    set pages 400

    \

    [order by]{#bookmark8}

    “데이터 정렬하는 절” ex)

    select ename, sal from emp

    order by sal asc;

    낮은값에서 높은값순으로 정렬 옵션:

    1\. asc → 낮은값에서 높은값

    2\. desc → 높은값에서 낮은값 순으로 정렬

    \

    [Column and row]{#bookmark9}

    테이블은 데이터를 저장하는 논리적 저장소 이고 컬럼(columns)과
    로우(row)로

    구성되어 있다

    \

    []{}

    dept 테이블로 확인

    select \* from dept;

    select empno. ename, job, sal, comm from emp; 실행순서 : from →
    select

    모든컬럼조회 select \*

    from emp;

    \

    [Table pretty]{#bookmark10}

     [SQL&gt; show lines ← 테이블 결과 출력 가로 사이즈]{.p}

-   SQL&gt; set lines 300

-   SQL&gt; set pages 400

    \

    [Distinct (removing duplication)]{#bookmark11}

-   select distinct job

-   from emp;

    \

    [SQL GATE install]{#bookmark12}

    install in cmd by administrator

    select \*

    from emp; (ctrl + enter)

    \

    문제6. 부서번호 중복제거 출력

    select distinct deptno f rom emp;

    \

    ex) select ename || ‘의 직업은’ || job from emp; **(그대로 복사x)**

    문제 7. SCOTT 의 부서번호는 10번 입니다. 라고 결과가 출력되게 하시오
    select ename || '의 부서번호는' || deptno || '입니다' from emp;

    문제 8. 아래와 같이 결과가 출력되게 하시오!

    select ename || '의 월급은 ' || sal || '입니다' from emp order by
    sal desc; 컬럼별칭 사용법

    select ename as “이름”, sal as “월급” from emp;

    문제 9. 이름과 연봉(sal\*12) 을 출력하는데 연봉이 높은 사원부터
    출력하고 컬럼명을 한글로 이름, 연봉으로 출력

    select ename as “이름”, sal\*12 as "연봉" from emp order by sal(or
    연봉) desc; 실행순서) from → select → order , Therefore you can
    refer 연봉 in the order phase 문제10. 이름, 월급, 직업을 출력하는데
    직업을 ABCD 순으로 출력되게 하고 컬럼명을 한글로 이름, 월급,
    직업으로 출력되게 하시오

    select ename as "이름", sal as "월급", job as "직업" from emp order
    by job asc; 문제 11. (점심시간 문제) 라인검사

     [아래와 같이 출력하는데 최근에 입사한 사원부터 출력되게
    하시오]{.p}

-   select ename || '의 입사일은' || hiredate || '입니다' as "사원정보"
    from emp order by hiredate desc;

    \

    [Null]{#bookmark13}

    1\. 데이터가 없는 상태

    2\. 알수 없는 값 (unknown) 예제 )

    select ename,sal, comm from emp;

    select ename, sal, comm, sal+comm

    from emp;

    왜 null을 만들었나?

    null이 존재하면 그룹함수를 사용할때 연산이 빨라지는 장점이 있다. 예)

    select sum(comm) from emp;

    \

    select sum(nvl(comm,0)) from emp;

    문제12. 이름, 월급, 커미션을 출력하는데 커미션이 null인 사원들은
    0으로 출력되게 하시오! select ename, sal, nvl(comm,0)

-   from emp;

    \

    [NVL Function(null value logic)]{#bookmark14}

    Null value logic

    ex) nvl(column, 0) : null 대신에 0을 출력

    문제13. 이름,월급,커미션, 월급+ 커미션을 출력하는데 요번달 월급을
    줄수 있도록 결과가 출력되게 하시오!

    select ename, sal, comm , sal+nvl(comm,0)

-   from emp;

\

[3 types of characters]{#bookmark15}

 [산술 연산자 : \*/ + -]{.p}

 [비교 연산자 : &gt;, &lt;, &gt;=, &lt;=, =, &lt;&gt;, !=, \^= (같지
않다 3가지)]{.p}

-   논리 연산자: and, or, not

    \

    [Chapter 2. Restricting and Sorting Data]{#bookmark16}

    2장 목차

    1\. where 절 사용법

    2\. 비교 연산자 사용법

    3\. 기타 비교 연산자 사용법

    4\. 논리 연산자 사용법

    5\. 연산자 우선순위

    \

    [where clause]{#bookmark17}

    “where 절은 데이터 검색조건을 기술하는 절”

    예제) select 컬럼

    from 테이블 where 검색조건문

    사원번호가 7788번인 사원의 사원번호와 이름을 출력하시오 3\~ select
    empno, ename

    1\~ from emp

    \

    2\~ where empno= 7788; (검색조건)

    앞에는 실험순서

    문제14. 월급이 3000인 사원의 이름과 월급을 출력하시오 select ename,
    sal

-   from emp

-   where sal=3000;

    문제15. 월급이 1500 이상인 사원들의 이름과 월급을 출력하시오 select
    ename, sal

-   from emp

-   where sal &gt;=2500;

    문제16. 연봉이 36000이상인 사원들의 이름과 연봉을 출력하는데
    컬럼명을 이름과 연봉으로 출력하시오

    select ename as “이름”, sal\*12 as “연봉”

-   from emp

-   where sal &gt;= 3000;

    sal 대신 연봉을 쓰면 출력안된다 왜냐하면 실행순서 때문에 (실행순서
    // from → where → select)

    문제17. 직업이 salesman 인 사원들의 이름과 직업을 출력하시오 select
    ename, job

-   from emp

-   where job=’SALESMAN’;

    문제 18. 월급이 1000에서 3000 사이인 사원들의 이름과 월급을
    출력하시오 select ename, sal

-   from emp

-   where sal &lt;= 3000 and sal &gt;=1000; selct ename, sal

-   from emp

-   where sal between 1000 and 3000;

    \

    [Comparison operator]{#bookmark18}

    1\. between and 연산자

    문제 19. 월급이 1000에서 3000사이가 아닌 사원들의 이름과 월급을
    출력하시오 select ename, sal

    from emp

-   where sal not between 1000 and 3000;

    \

    [Date type check]{#bookmark19}

    년도 데이터를 검색할때에는 현재 내가 접속한 프로그램에 날짜 형식이
    어떻게

    되어있는지 확인을 하고 날짜 검색을 해야 제대로 검색할수 있다[.
    ]{.s8}확인하는 방법?

    select \*

    from nls\_session\_parameters;

    NLS stands for national language support 동양 서양 날짜형식 주의
    필요

    문제 20. 81년 12월 11일에 입사한 사원의 이름과 입사일 출력 select
    ename, sal

    from emp

    where hiredate='11/Dec/81';

    \

    문제 21. 1981 년에 입사한 사원들이 이름과 입사일을 출력 select
    ename, hiredate

-   from emp

-   where hiredate between '1/Jan/81' and '31/Dec/81';

    문제 22. 직업이 SALESMAN 이 아닌 사원들의 이름과 직업을 출력하시오.
    select ename, job

    from emp

    where job !='SALESMAN';

    \

    문제23. 부서번호가 30번이 아닌 사원들의 이름과 부서번호 출력 select
    ename, deptno

    from emp where deptno !=30;

    \

    1.  between and

    2.  like

    3.  in

    4.  is null

        [like operator]{#bookmark20}

        ex) 이름의 첫번째 철자가 s로 시작하는 사원들의 이름을
        출력하시오!

        \

        select ename

-   from emp

-   where ename like ‘S%’;

    (% : wild card 이 자리에 뭐가 와도 관계 없다. wild card 로
    인식되려면 꼭 like 로 써야함)

    \

    [문자는 single quotation mark 필요]{#bookmark21}

    숫자는 필요 없음

    문제24. 이름의 끝글자가 T로 끝나는 사원이름 출력 select ename

    from emp

    where ename like '%T';

    문제25. 이름의 두번째 철자가 M인 사원들의 이름을 출력하시오! select
    ename

-   from emp

-   where ename like ‘\_M%’;

    ! like 연산자를 사용할때 쓰는 키워드

     [\_ : 이자리에 어떤게 와도 관계없는데 자릿수는 한자리 문제 26.
    이름의 세번째 철자가 L인 사원이름 출력]{.p}

    select ename from emp

    where ename like ' L%';

    문제 27. 81년도에 입사한 사원들의 이름과 입사일을 출력하는데 between
    and 쓰지 말고 select ename, hiredate

-   from emp

-   where hiredate like '%81';

    아래의 insert문을 실행해서 데이터를 입력하시오 insert into
    emp(empno, ename, sal)

    values( 1234, ‘A%B’, 3500);

    commit;

    문제 28. 이름의 두번째 철자가 %인 사원을 출력하시오 select ename

-   from emp

-   where ename like '\_m%%' escape 'm';

    \

    문제 29. 이름의 두번째 철자와 세번째 철자 %인 사원의 이름 출력

    \

    select ename

-   from emp

-   where ename like '\_m%m%%' escape 'm';

    문제 30. 이름의 첫번째 철자가 S로 시작하지 않는 사원 이름 출력
    select ename

-   from emp

-   where ename not like 'S%';

    \

    [in operator]{#bookmark22}

    문제 31. 사원번호가 7788,7902, 7369 번인 사원들의 사원번호와 이름을
    출력하시오

    select empno, ename

-   from emp

     [where empno in (7788,7902,7369);]{.p}

    문제 32. 직업이 salesman, analyst 인 사원들의 이름과 직업을
    출력하시오 \~ select ename, job

-   from emp

-   where job='SALESMAN' or job='ANALYST'; select ename, job

-   from emp

-   where job in('SALESMAN' ,'ANALYST');

    문제 33. 직업이 SALESMAN, ANALYST 가 아닌 사원들의 이름과 직업을
    출력 select ename,job

-   from emp

-   where job not in ('SALESMAN','ANALYST');

    문제 34. comm 이 null 인 사원들의 이름과 커미션 출력 SELECT ename,
    comm

    from emp

    where comm is null;

    pb. 35. print out job, commission of employees whose job is SALESMAN
    and whose commission is not null and sort it in descending order,
    and make

    문제 35. comm이 null 아니고 직업이 SALESMAN인 사원들의 이름과 월급과
    직업과 커미션을 출력하는데 커미션이 높은 사원부터 출력하고 컬럼명을
    이름, 월급, 직업, 커미션 한글로 출력되게 하시오

    SELECT ename as "이름", sal as "월급", comm as "커미션" from emp

    \

    where comm is not null and job='SALESMAN'

    order by comm desc;

    \

    [Database connection to team leader using Gate]{#bookmark23}

    192.168.19.3

    유저이름: scott 패스워드: tiger 서비스이름: xe 접속모드: default

    ALTER SESSION SET nls\_date\_format ='RRRR/MM/DD'; INSERT INTO EMP2

    VALUES(5,'정호진',32,'1987/09/22','물리학','tbop02@gmail.com','010-2985-
    9834','서울시 광진구 화양동','LGT');

    COMMIT;

    문제 36. 이름과 전공과 나이를 출력하는데 나이가 높은 학생부터 SELECT
    ename,major, age

-   FROM EMP2

-   ORDER BY age DESC;

    문제 37. 나이가 27에서 32사이인 학생들의 이름과 나이와 전공과 주소를
    출력하시오 SELECT ename, age, major, address

-   FROM EMP2

-   WHERE age BETWEEN 27 AND 32; (where age &gt;=27 and age &lt;=32;)
    문제 38. 성이 김씨인 학생들의 이름과 나이를 출력하시오

    SELECT ename,age

-   FROM EMP2

-   WHERE ename LIKE '김%';

    problem 39. print name and major of students whose majo SELECT
    ename, major

    문제 39. 전공이 컴퓨터 관련 학과가 아닌 학생들의 이름과 전공

-   FROM EMP2

-   WHERE major NOT LIKE '%컴퓨터%';

    \

    [logic operator]{#bookmark24}

    and, or, not

    \

    True and Null → Null

    (because we do not know whether Null is True or False)

    True or Null → True

    (no matter what Null is, answer should be True) False or Null → Null

    False and Null → False

    \

    problem 40. print name, salay and job of employees whose job is
    SALESMAN and whose salary is more then 1200.

    SELECT ename, sal, JOB FROM EMP

    where sal &gt;= 1200 and job=’SALESMAN’;

    \

    Problem 41.print name, salary and department number of employees
    whose commission is null and dept.

    SELECT ename, sal, deptno FROM EMP

    WHERE COMM IS null AND deptno=20;

    \

    problem 42. print name, age and major of students whose major is
    related to computer and whose age is 20s.

    SELECT ename, age ,major FROM EMP2

    WHERE major LIKE '%컴퓨터%'

    AND age between 20 and 29; (do not use age like ’2%’)

    문제 43. print out name, address and telecom company of students
    whose city is seoul and whose telecom company is SK.

    주소가 서울이면서 통신사가 sk인 학생들의 이름과 주소와 통신사를
    출력하시오. Problem 43. print name, address and telecom

    SELECT ename,address, telecom FROM EMP2

    WHERE address LIKE '서울%' AND telecom like 'sk%;

    [user creation]{#bookmark25}

    create user scott

-   identified by tiger; grant dba to scott;

    (give dba permission to scott) show user;

    (confirm user name)

    sqlplus scott/tiger (connect as scott)

    link

    create database link our\_class\_link connect to scott

    identified by tiger

    using ’192.168.19.3:1521/xe’;

    create table emp2 as

    select \* from emp2@our\_class\_link;

    Problem 44. print name, age and major of students whose major is not
    related to computer, and sort by age in descending order and change
    column name to 이름, 나이 and 전공.

    SELECT ename, age, major FROM EMP2

    WHERE major NOT LIKE '%컴퓨터%'

    ORDER BY age DESC;

    \

    [Priority of operator]{#bookmark26}

-   priority of logic operator ex)

    select ename, sal, job

-   from emp

-   where job=’SALESMAN’

-   or job=’ANALYST’

-   and sal &gt; 1500;

which logic operator will be executed first? answer) and

problem 55. change the above query as ‘or’ can be executed first.

\

→ just use parentheses

\

[Charpter 3. Function]{#bookmark27}

the reason why function is necessary when you search for something is
that if you use function, you can search for variety of data.

ex) how much students in my class use Naver email

-   what is the most frequent telecom students in my class use

    1.  single row function

-   character data : upper, lower, initcap, substr, instr, replace,
    concat, lpad, rpad, ltrim, rtrim, trim

-   number data : round, trunc, mod

-   date values : months\_between, add\_months, next\_day, last\_day

-   변환 : to\_char, to\_number, to\_date

-   일반 : nvl, nvl2, decode, case problem 46. query the below sql, then
    see.

SELECT UPPER(ename), LOWER(ename), INITCAP(ename) FROM EMP;

[Substr]{#bookmark29}

Extract a sting of determined length

query)

select ename, substr(ename, 1, 3)

o[ ]{.s12}[from emp; result)]{.p}

KING → KIN

// from first character, take 3 characters

Problem 47. print name and first character of the name SELECT ename,
SUBSTR(ename, 1, 1)

FROM EMP2;

Problem 48. print name and age of our class students whose given name is
‘이’ SELECT ename, age

FROM EMP2

WHERE SUBSTR(ename,1,1) = '이';

\

[another example of substr]{#bookmark30}

SELECT ename, SUBSTR(ename, -2,2)

FROM EMP2;

→ Minus counts order from end of sentence

Problem 49. print addresses from our class table like below SELECT
ename, SUBSTR(address, -3, 3)

FROM EMP2;

\

[instr function]{#bookmark31}

return the numerical position of a named character ex)

select ename, instr(ename,’L’)

o[ ]{.s12}[from emp;]{.p}

Problem 50. print email, numerical position of @ of email. SELECT email,
INSTR(email,'@')

FROM EMP2;

\

Problem 51. print sting after ’@’ of emails from our class table SELECT
SUBSTR(email,INSTR(email,'@')+1)

FROM EMP2;

\

[replace function]{#bookmark32}

replace a named character with another named chacracter

ex)

select ename, replace

\

[regexp\_replace function]{#bookmark33}

replace but using regular expression

ex)

SELECT ename, regexp\_replace(sal,'\[0-2\]','\*')

o[ ]{.s12}[FROM EMP;]{.p}

\

[Trim]{#bookmark34}

\

cut specific charater ex)

[when email=’](mailto:eee@eee.com){.s13}eee@eee.com’ rtrim(email,
‘.com’);

→ eee@eee

Trim function example

before problems, insert this one insert into emp(empno, ename, sal)
[o]{.s11}[ ]{.s12}values(2035, ’JANE ‘,4500);

ex)

SELECT ename, sal

-   FROM EMP

    WHERE TRIM(ename)='JANE';

    \

    trim(ename) → trim leading and trailing characters from a character
    string rtrim(ename) → trim trailing characters from a character
    string ltrim(ename) → trim leading characters from a character
    string

    \

    [Concat]{#bookmark35}

    concatenate two columns’ data

    ex) select concat(ename,sal) from emp;

    [lpad, rpad]{#bookmark36}

    Returns an expression left-padded to length of n characters with a
    character

    expression

    Returns an expression right-padded to length of n characters with a
    character expression

    ex) select ename, rpad(sal, 10, ‘\*’) from exp;

    \

    [lengthon]{#bookmark37}

    Return the number of characters in the expression

    ex) select ename, length(ename) from emp;

    \

    Problem 54, print out name and the number of characters of name of
    employees whose number of characters of name is equal or more
    than 5.

    SELECT ename, LENGTH(ename) FROM EMP

    WHERE LENGTH(ename)&gt;=5

    \

    Problem 55. print out name, address and length of address but order
    the print data in descending order

    SELECT ename, address, LENGTH(address) FROM EMP2

    ORDER BY LENGTH(address) DESC;

    \

    [Number]{#bookmark38}

    round, trunc, mod

    \

    [Round]{#bookmark39}

    select 2567.56, round(2567.56,1)

    from dual; // dual is a virtual table because columns has to do with
    nothing

    → 2567.6

    // Rounds value to a specified decimal

    \

    [trunc]{#bookmark40}

    SELECT 2567.56, trunc(2567.56,-1)

    \

    FROM dual;

    → 2560

    \

    [mod]{#bookmark41}

    finds the remainder of the argument divided by the second argument

    ex) select mod(10,3)

    -   from dual;

        →1

        \

        [power function]{#bookmark42}

        power(x,y)

        return x to the y select power(2,3)

    -   from dual;

        → 8

        \

        Problem 56.

        SELECT SUBSTR(email,1,INSTR(email,'@')-1)

    -   FROM EMP2;

        \

        [Date functions]{#bookmark43}

        months\_between, add\_months, next\_day, last\_day date - date =
        number

        date - number=date date + number=date

        \

        [Current date]{#bookmark44}

        ex)

        select sysdate from dual

        Pb 57. print out how many days employees has worked so far since
        hired SELECT ROUND(sysdate-hiredate)

    -   FROM emp;

        Pb 58. print out how many months employees has worked so far
        since hired select ename, months\_between(sysdate,hiredate)

        \

    -   from emp;

Pb 59. print out the date after 100 months from now. SELECT SYSDATE,
add\_months(sysdate,100)

FROM EMP;

Pb 60. print out the date of following Monday. SELECT SYSDATE,
NEXT\_DAY(SYSDATE,'mon') FROM DUAL;

Pb 61. print out the date of following Monday after 100 months SELECT
NEXT\_DAY(add\_months(sysdate,100),'Mon')

FROM DUAL;

Pb 62. print out last day of this month. SELECT SYSDATE,
LAST\_DAY(sysdate)

FROM DUAL;

Pb 62. print out how many days left in this month SELECT
last\_day(sysdate)-SYSDATE

FROM DUAL;

\

[Case]{#bookmark45}[conversion functions]{.s6}

There are 3 types of data

1.  character

2.  numeric

3.  date

\

[Internal query checking]{#bookmark46}

set autot on

\

[]{}

oracle automatically convert wrong query But do not use this one for
performance

Another example select ename, sal

from emp

where sal like ’30%’;

\

As ‘30%’ can not be converted to character for %, so oracle change sal
type to numeric

type

In SQL gate, push Ctrl+Alt+F7 to see internal process after drag

\

[]{}

[2 types of data conversion]{#bookmark47}

1.  Implicit conversion ex) select ename, sal

    -   from emp

    -   where sal like ’30%’

        It’s usually bad for performance.

        Mysql or Mssql do not support implicit type conversion

2.  Explicit conversion

    → explicitly change data type

    1.  to\_char

    2.  to\_number

    3.  to\_date

-   ex) SELECT sal, TO\_CHAR(sal)

-   FROM EMP;

-   ex) SELECT sal, TO\_CHAR(sal,'999,999')

-   FROM EMP;

-   // 9 mean decimal point and any number can be put into this
    position.

    \

    []{}

    \

    Pb 64. print out name and salary\*2093045 and make it easier to see

    이름과 salary\*2093045 를 보기편하게 출력하라.

    SELECT ename, TO\_CHAR(sal\*2093045,'999,999,999,999') FROM EMP;

    Pb. 65. print out today’s day. SELECT TO\_CHAR(SYSDATE,'day') FROM
    DUAL;

    Pb 66. print out the day of your birth

    select ename,TO\_CHAR(birth,'day') FROM EMP2

    WHERE ename='정호진';

    Pb 67. print out name,birth and address of students whose birth day
    is Saturday. select ename, birth, address

    FROM EMP2

    WHERE TRIM(TO\_CHAR(birth,'day'))='Saturday'; Pb 68. print out day
    of date after 100 months.

    \

    [Date format]{#bookmark48}

    1.  year : RRRR, RR, YYYY, YY

    2.  Month : MM, Mon

    3.  date : dd

    4.  day : day, dy

    5.  hour : HH, HH24

    6.  minute : MI

    7.  second : SS

    8.  week : WW, IW

    \

    pb 69. print out name and commission of Emp table.

    pb 70. print out name and commission but if null, convert it to 0.
    SELECT ename, REPLACE(NVL(comm,'-1'),'-1','no comm')

    FROM EMP;

    or

    SELECT ename, nvl(to\_char(comm),’no\_comm’) FROM EMP;

    \

    // if you use nvl(comm,’no comm’), error occur because ‘no comm’ can
    not be converted

    to numeric.

    Pb 72. print out name and mgr(manager administration number but if
    null, replace it with ‘no manager’

    select name,

    Pb 73. print out like the below

    SELECT ename || '의 커미션은' || nvl(comm,0) || '입니다' FROM EMP

    ORDER BY nvl(comm,0) desc;

    Pb 74. print out name, comm order by comm in ascending order 이름
    커미션을 출력하는데 커미션이 높은 사원부터 출력하시오.

    SELECT ename, comm FROM EMP

    ORDER BY comm DESC nulls last;

    Pb 75. print out name and commission in ascending order but null is
    first. SELECT ename, COMM

    FROM Emp

    ORDER BY COMM ASC nulls FIRST;

    Pb 76. print out name and hiredate of employees whose hiredate is
    Sep 10th in 1981. 81년 9월 10일에 입사한 사원들의 이름과 입사일을
    출력하시오!

    SELECT ename, hiredate FROM EMP

    WHERE TO\_CHAR(hiredate,'RR/MM/DD')='81/09/10';

    Current session format alternation

    ALTER SESSION SET nls\_date\_format='RR/MM/DD';

    // session : current connection environment

    &gt;SELECT ename, hiredate

-   FROM EMP

-   WHERE hiredate='81/09/10'; ok!

    \

    [Difference between RR and YY as date format]{#bookmark49}

    RR chose nearest year

    ex) 1981 vs 2081 → 1981

    \

    YY choose current century

    ex) 1981 vs 2081 → 2081

    \

    [To\_char vs format change]{#bookmark50}

    SELECT ename, hiredate

    FROM EMP

    WHERE TO\_CHAR(hiredate,'YY/MM/DD')='81/09/10';

    do not change left-handed thing 좌변 절대 바꾸지 말것

    This way!

    &gt;&gt;&gt;&gt;&gt;&gt;

    SELECT ename, hiredate FROM EMP

    WHERE hiredate=TO\_DATE('81/09/10','RR/MM/DD')

    &gt;&gt;&gt;&gt;&gt;&gt;

    Advantages

    1.  alter session X

    2.  to\_char X

        \

        [To\_number]{#bookmark51}

        create table emp05

        ( ename varchar2(20), sal varchar2(20));

        insert into emp05 values(‘scott’, ’3000’); insert into emp05
        values(‘smith’,’1500’); commit;

        &gt;&gt;&gt;&gt; SELECT \*

        FROM emp05 WHERE sal=3000;

        //even though salary input is numeric in where part, result will
        come out because of internal auto correction.

        \

        [general function]{#bookmark52}

        nvl, nvl2, decode, case

        [nvl2]{#bookmark53}

        ex) select ename, sal, comm, nvl2(comm, sal+comm, sal)

        from emp;

        // Return sal+comm if comm is null, otherwise sal.

        Decode

        // kind of conditional print out

        ex) print out name, salary , department number and bonus but if
        dept. no. is 10, print out 6000, if 20, 3400, other than
        that, 0.

        select ename, sal, deptno,

-   decode(deptno, 10, 6000,

     [20, 3400,0)]{.p}

-   from emp;

Pb 78. print out name, majar, salary and bonus but if job is salesman,
bonus should be 10000, other than that, print out 0.

SELECT ename,job,sal, DECODE(job,'salesman',10000,0) AS "보너스" FROM
EMP;

\

Case

print out name, age and bonus but if age is equal to or more than 30,
bonus should be

5000, other then that, 0.

이름, 나이, 보너스를 출력하는데 나이가 30살 이상이면 보너스를
5000출력하고 나머지 나이는 30보다 작으면 0을 출력하시오

Pb 79. print out name, age and bonus but if age is equal to or less than
25, print out 6000 as bonus, if 26\~30, 8000, if equal to or more than
30, 9000.

SELECT ename,age,

CASE WHEN age&lt;=25 THEN 6000

When age BETWEEN 26 AND 29 THEN 8000

else 9000 end

FROM EMP2;

\

Chapter 5. Group function

1.  max

2.  min

3.  sum

    \

4.  avg

5.  count

6.  having

7.  group overlapping

“The group functions process a number of columns and return one result.”

\

[Max]{#bookmark54}

\

EX) select max(sal)

-   from emp;

    Pb 80. print out maximum salary among employees whose job is
    SALESMAN. SELECT job, MAX(sal) // 4

    FROM EMP // 1

    WHERE job='SALESMAN'; //2

    group by job; //3 → means grouping error query)

    select job, max(sal) from emp

    where job=’SALESMAN’;

    SELECT job,MAX(sal) FROM EMP

    GROUP BY job;

    Pb 81. print out dept. No. and maximum salary according to dept. No.
    부서번호, 부서번호별로 최대월급을 출력하시오.

    SELECT deptno, MAX(sal) //3 from EMP //1

    GROUP BY deptno; //2

    Pb 82. print out the above one except for dept. no. 1 SELECT deptno,
    MAX(sal)

    from EMP

    WHERE deptno!=30 GROUP BY deptno;

    coding order is important but process order is different from what
    you put

    Pb 83. print out job and maximum salary but exclude SALESMAN and
    order by maximum salary.

    SELECT job,MAX(sal) //4

    \

    FROM EMP //1

    WHERE job!='SALESMAN' //2

    GROUP BY job //3

    ORDER BY MAX(sal) DESC; //5

    Pb 84. print out telecom and maximum age group by telecom SELECT
    telecom, MAX(age)

    FROM EMP2

    GROUP BY telecom;

    Pb 85. print out major and maximum age according to major SELECT
    major, MAX(age)

    FROM EMP2

    GROUP BY major;

    \

    [Min]{#bookmark55}

    \

    Problem 86 -

    Pb 86. print out minimum salary. SELECT min(sal)

    FROM EMP;

    Pb 87. print out job and minimum salary according to job. SELECT
    job, MIN(sal)

    FROM EMP GROUP BY job;

    Pb 88. print out the above result but sort in descending order

    SELECT job, MIN(sal) FROM EMP

    GROUP BY job

    ORDER BY MIN(sal) desc;

    Pb 89. From the above result, exclude ‘salesman’ SELECT job,
    MIN(sal)

    FROM EMP

    WHERE job!='SALESMAN' GROUP BY job

    ORDER BY MIN(sal) desc;

    Pb 90. print out age and the number of students according to age,
    and sort it in descending order, and change column name to 나이 and
    건수.

    \

    SELECT age AS "나이", COUNT(age) AS "건수"

    FROM EMP2 GROUP BY age

    ORDER BY age DESC;

    \

    [recap]{#bookmark56}

    select query

    -   select

    -   from

    -   where

    -   group by [o]{.s11}[ ]{.s12}order by function

    -   single row function : character, numeric, date, conversion,
        general

    -   multi row function : max, min, ave, sum, count

    Pb 91. print out name, age of students whose major is not related to
    computer, and sort it in descending order.

    SELECT ename, age FROM emp2

    WHERE major NOT LIKE '%컴퓨터%'

    ORDER BY age DESC;

    Pb 92. print out department number and maximum salary according to
    department number but exclude department is 20, and sort it in
    descending order of maximun salary

    SELECT deptno, MAX(sal) FROM EMP

    WHERE deptno != 20

    GROUP BY deptno ORDER BY MAX(sal) DESC;

    or)

    SELECT deptno, MAX(sal) as 최대월급 FROM EMP

    WHERE deptno != 20 GROUP BY deptno

    ORDER BY 최대월급 DESC;

    \

    // if there is no space in as name, dont have to use quotation but
    if use \_ or \$,

    double quotation mark is necessary

    [Avg ground function]{#bookmark57}

    “Average”

    \

    [null ignoring issue]{#bookmark58}

    Group function ignore null value

    ex) select avg(sal) from emp;

    -----------------------------------

    sal 3000

    2000

    null 1000

    -----------------------------------

    → 2000

    //just ignore null value in oracle.

    \

    Pb 93. query the names and commission of all employees in EMP table.

    -   SELECT ename,comm

    -   FROM EMP;

        Pb 94. print out name and job of employees whose commission is
        not null.

    -   SELECT job

    -   FROM EMP

    -   WHERE COMM IS NOT NULL; Pb 95. print out the above again but

    -   SELECT DISTINCT(job)

    -   FROM EMP

    -   WHERE COMM IS NOT NULL;

        Pb 96. query the average commission of all employees

    -   SELECT AVG(comm)

    -   FROM EMP;

        Pb 97. query the average commission but divide it by 14, not 4.

    -   SELECT AVG(NVL(comm,0))

    -   FROM EMP;

        \

        Pb 98. Is the below two query the same or not?

        1.  select sum(comm) from emp;

        2.  select sum(nvl(comm,0)) from emp;

    -   // a’s performance is better

        Pb 99. print out the jobs and average salary and sort it in
        descending order of the average salary.

    -   SELECT job, AVG(sal)

    -   FROM EMP

    -   GROUP BY job

    -   ORDER BY AVG(sal) DESC;

        Pb 100. print out job and average salary but only if average
        salary is equal to or more than 4000.

    -   // can not use group function in where clause

    -   Use Having clause after group clause!!!

    -   SELECT job, avg(sal)

    -   FROM EMP

    -   GROUP BY job

    -   HAVING AVG(sal)&gt;=4000;

\

[Group function in search query]{#bookmark59}

→ just use having

Pb 101. print out department number and minimum salary according to
department number but only if equal to or more than 2000.

SELECT deptno, MIN(sal) FROM EMP

GROUP BY deptno HAVING MIN(sal)&gt;=2000;

\

Coding order & processing order

5 select

1.  from

2.  where

3.  group by

4.  having

5.  order by

    \

    Pb 102. print out job and total salary of employees whose job is not
    SALESMAN but

    only if total salary &gt;=5000, and sort it in descending order of
    total salary.

    -   SELECT job, SUM(sal)

    -   FROM EMP

    -   WHERE job !='SALESMAN'

    -   GROUP BY job

    -   HAVING SUM(sal)&gt;=5000

    -   ORDER BY SUM(sal) DESC;

        Pb 103. print the above result but use thousand seperator to the
        total salary.

    -   SELECT job, to\_char(SUM(sal),’99,999)

    -   FROM EMP

    -   WHERE job !='SALESMAN'

    -   GROUP BY job

    -   HAVING SUM(sal)&gt;=5000

    -   ORDER BY SUM(sal) DESC;

        //do not use this query

    -   SELECT job, to\_char(SUM(sal),’99,999)

    -   FROM EMP

    -   GROUP BY job

    -   HAVING job != ‘SALESMAN’ and SUM(sal)&gt;=5000 // do not use job
        condition in this in terms of performance

    -   ORDER BY SUM(sal) DESC;

        // job != ‘SALESMAN’ ← use in where clause

        Pb 104. print out name, hired date and hired year (4character)

    -   SELECT ename, hiredate, TO\_CHAR(hiredate,'RRRR')

    -   FROM EMP;

        Pb 105. print out hired date(4digit) and total salary according
        to the hired date.

    -   SELECT TO\_CHAR(hiredate,'RRRR'), SUM(Sal)

    -   FROM EMP

    -   GROUP BY TO\_CHAR(hiredate,'RRRR');

        Pb 106. print out hired date(4digit), total salary, average
        salary, maximum salary and minimum salary according to the hired
        date.

    -   SELECT TO\_CHAR(hiredate,'RRRR'), SUM(Sal), AVG(sal),
        MAX(sal),MIN(sal)

    -   FROM EMP

    -   GROUP BY TO\_CHAR(hiredate,'RRRR');

        \

        [Count (Group function)]{#bookmark60}

    -   “count rows”

    -   ex)

    -   select count(empno)

    -   from emp;

    -   → total rows

    -   ex)

    -   select count(\*)

    -   from emp;

    -   → total rows

    -   ex) select count(comm)

    -   from emp;

    -   → only rows which doesn’t include null value

        Pb 107. print out job and the number of employees according to
        the job

    -   SELECT job, COUNT(\*)

    -   FROM EMP

    -   GROUP BY job;

        Pb 108. print job and the number of employees according to job
        but only in case the number of employees is equal to or more
        than 4.

    -   SELECT job, COUNT(\*)

    -   FROM EMP

    -   GROUP BY job

    -   HAVING COUNT(\*) &gt;=4;

        Pb 109. print job and the number of employees according to job
        but only in case the number of employees is equal to or more
        than 4, and sort it in descending order of the number of
        employees according to job

    -   SELECT job, COUNT(\*)

    -   FROM EMP

    -   GROUP BY job

    -   HAVING COUNT(\*) &gt;=4

    -   ORDER BY COUNT(\*) DESC;

        Pb 110. print out the above again, but exclude the case that job
        is SALESMAN

    -   SELECT job, COUNT(\*)

    -   FROM EMP

        \

    -   WHERE job !='SALESMAN'

    -   GROUP BY job

    -   HAVING COUNT(\*) &gt;=4

    -   ORDER BY COUNT(\*) DESC;

        Pb 111. print out the number of students whose major is related
        to statistics

    -   SELECT COUNT(\*)

    -   FROM EMP2

    -   WHERE major LIKE '%통계%'; Pb 112. (lunch time problem)

    -   SELECT SUBSTR(address,1,3),COUNT(\*)

    -   FROM EMP2

    -   GROUP BY SUBSTR(address,1,3)

    -   ORDER BY COUNT(\*) DESC;

        \

        [difference between where and having]{#bookmark61}

    -   where : general search

    -   having : Group search

        \

        [Nesting group functions]{#bookmark62}

        Pb 113. print out job without overlap, and count it.

    -   SELECT COUNT(DISTINCT job)

    -   FROM EMP;

        Pb 114. query the number of kind of ages.

    -   SELECT COUNT(DISTINCT age)

    -   FROM EMP2;

        Pb 115. print out the job and average salary according to jobs.

    -   SELECT AVG(Sal)

    -   FROM EMP

    -   GROUP BY job;

        Pb 116. print out the maximum average salay from the above
        result

    -   SELECT max(AVG(Sal))

    -   FROM EMP

    -   GROUP BY job;

        \

        Pb 117. print out the number of employees of job who has maximum
        number of

        employees.

    -   SELECT max(COUNT(\*))

    -   FROM EMP

    -   GROUP BY job;

        Pb 118. 위의 결과중 가장 인원수가 많은 직업을 무엇인지?

        Pb 119. print out dept. no. and total salaries according to
        dept.no. ( do you need horizontal out? think about it)

        Pb 119. 부서번호, 부서번호별 토탈 월급 출력(그룹 함수결과 세로→
        가로) 필요? 생각해보자

        SELECT deptno, SUM(sal)

        FROM EMP

        GROUP BY deptno;

        Pb 120. print out salaries of employees whose department number
        is 30. Pb 120. 부서번호가 30번인 사원들의 월급만 출력하시오

    -   SELECT sal

    -   FROM EMP

    -   WHERE deptno=30; pb 121. query the below

    -   select decode (deptno, 10, sal,0)

    -   from emp;

        pb 122. sum the above result.

    -   select SUM(decode(deptno, 10, sal,0))

    -   from emp;

        pb 122. 직업,직업별 토탈월급을 출력하는데 아래와같이 출력하시오

    -   select sum(decode(job, 'SALESMAN',sal ,0)) AS "SALESMAN" ,

    -   sum(decode(job, 'CLERK',sal,0)) AS "CLERK",

    -   sum(decode(job,'PRESIDENT',sal,0)) AS "PRESIDENT"

    -   from emp; Pb 123.

        Pb 123. 입사한 년도, 입사한 년도별 토탈월급을 출력하시오 SELECT

        SUM(DECODE(TO\_CHAR(hiredate,'RRRR'),'1980',sal,0)) AS "1980",

        SUM(DECODE(TO\_CHAR(hiredate,'RRRR'),'1983',sal,0)) AS "1983",

        SUM(DECODE(TO\_CHAR(hiredate,'RRRR'),'1982',sal,0)) AS "1982",

        \

        SUM(DECODE(TO\_CHAR(hiredate,'RRRR'),'1981',sal,0)) AS "1981"

        FROM EMP; Pb 124.

        select job,

        sum(decode(deptno, 10, sal,0)) AS "10" ,

        sum(decode(deptno, 20, sal,0)) AS "20",

        sum(decode(deptno, 30, sal,0)) AS "30" from EMP

        GROUP BY job;

        \

        []{}

        \

        [pivot, unpivot]{#bookmark63}

        horizontal → vertical // vertical → horizontal

        1.  pivot

        2.  unpivot

        Pb 125. print out department number and total salaries according
        to department number horizontally

        Pb 125. 부서번호, 부서번호별 토탈월급을 가로로 출력.

    -   3// SELECT \*

    -   1// FROM ( SELECT deptno, sal FROM emp) → after putting

        []{}

    -   2// pivot( SUM(sal) FOR deptno IN (10,20,30));

        \

        Pb 126. print out job and total salaries according to the job
        horizontally using pivot Pb 126. 직업, 직업별 토탈월급을
        출력하는데 pivot을 써서 가로로 출력하시오!

    -   SELECT \*

    -   FROM (SELECT job,sal FROM emp)

    -   pivot (SUM(sal) FOR job IN
        ('SALESMAN','CLERK','PRESIDENT','MANAGER','ANALYST'));

        Pb 127. just query for update update emp2

        set telecom ='lg'

        \

        where telecom in ('LG','uplus','LGU+','LGT');

        commit; update emp2

        set telecom ='kt' where telecom ='KT'; commit;

        update emp2

        set telecom ='cjh' where telecom='CJH'; commit;

        2 전공 데이터 정재 update emp2

        set major='컴퓨터공학'

        where major='컴퓨터 공학'; select major

        from emp2

        order by major asc; update emp2

        set major='경영정보학' where major='경영정보'; update emp2

        set major='기술융합공학' where major='기술융합공학과'; update
        emp2

        set major='시스템경영공학' where major='시스템경영공학부';
        commit;

        Pb 127. 통신사, 통신사별 인원수를 출력하는데 통신사별 인원수가
        높은것부터 출력하시오!

    -   SELECT telecom, COUNT(\*)

    -   FROM EMP2

    -   GROUP BY telecom

    -   ORDER BY COUNT(\*) DESC;

        Pb 128. print the above out rotated by 90 degree

    -   SELECT \*

    -   FROM (SELECT telecom FROM EMP2)

        \

    -   pivot ( COUNT(telecom) FOR telecom IN ('kt','lg','sk','cjh'));

Pb 129. SELECT \*

FROM (SELECT major,age FROM EMP2)

pivot ( COUNT(\*) FOR age IN (24,25,26,27,28,29,32));

\

[]{}

\

[Data analysis function]{#bookmark64}

Data analysis function helps analyze data which is not easily solved by
existed function.

1.  rank

2.  dense\_rank

3.  ntile

4.  accumulated data output

5.  pivot

6.  unpivot

\

[Rank]{#bookmark65}

ex)

SELECT ename, sal,

RANK() OVER (ORDER BY sal desc) 순위 FROM EMP;

\

[]{}

Pb. 130.

SELECT ename,age,

RANK() OVER (ORDER BY age desc) 순위 FROM EMP2;

\

[]{}

\

[Dense\_rank (removing degeneracy)]{#bookmark66}

SELECT ename,age,

dense\_RANK() OVER (ORDER BY age desc) 순위 FROM EMP2;

[]{}

\

Pb 131.

SELECT ename,sal,

DENSE\_RANK() OVER(ORDER BY sal desc) 순위 FROM EMP

[]{}

WHERE job='SALESMAN';

\

Pb 132. 월급이 1000에서 3000사이인 사원들의 이름과 월급과 입사일과
순위를 출력하는데 순위가 먼저 입사한 사원부터 순위를 부여하시오

SELECT ename, sal,hiredate,

DENSE\_RANK() OVER (ORDER BY hiredate asc) 순위 FROM EMP

WHERE sal BETWEEN 1000 AND 3000;

\

[]{}

pb 133. 월급이 300인 사원은 사원 테이블에서 월급의 순위가 어떻게 되는가?
select

[]{}

dense\_RANK(3000) within group (ORDER BY sal desc) 순위 FROM EMP;

\

pb 134. SELECT

DENSE\_RANK(25) WITHin GROUP (ORDER BY age desc) 순위

\

[]{}

FROM EMP2;

\

Pb 135. 통신사, 이름, 나이 순위를 출력하는데 각 통신사별 나의에 따라
순위를 메겨 출력하시오.

SELECT telecom, ename, age,

RANK() OVER (PARTITION BY telecom order BY age desc) 순위 FROM EMP2;

Pb 136. 직업, 이름, 월급, 순위를 출력하는데 순위가 직업별로 각각 월급이
높은 순서대로 순위를 출력하시오!

SELECT job,ename,sal,

dense\_RANK() OVER (PARTITION BY job ORDER BY sal desc) 순위 FROM EMP;

[]{}

Pb. 137. 전공, 이름, 나의, 순위를 출력하는데 순위가 전공별로 각각 나이가
높은 학생부터 순위가 출력되게 하시오.

SELECT major, ename, age,

DENSE\_RANK() OVER(PARTITION BY major ORDER BY age desc) 순위 FROM EMP2;

\

[]{}

Pb 138. 위의 결과에서 순위가 1위인 학생들만 출력.

\

[Sub query in from clause]{#bookmark67}

SELECT \*

FROM(SELECT major, ename, age,

dense\_RANK() over (PARTITION BY major ORDER BY age desc) AS 순위 FROM
EMP2

)WHERE 순위=1;

\

[]{}

\

Pb 139, 직업, 이름, 월급, 순위를 출력하는데 직업별로 각각 월급의 순위가
1위인

사원들만 출력하시오. SELECT \*

FROM (

SELECT job,ename, sal,

DENSE\_RANK() OVER (PARTITION BY job ORDER BY sal desc) 순위 FROM EMP

)

WHERE 순위=1;

\

[]{}

\

ntile

\

“divide a column into n” ex)

select ename, sal,

[]{}

ntile(4) over (order by sal desc) 등급 from emp;

\

Pb. 140. 통신사, 이름, 나이, 등급을 출력하는데 등급을 통신사별로 각각
등급을 나누는데 4등급으로 등급을 나누시오

SELECT telecom, ename,age,

NTILE(4) OVER (PARTITION BY telecom ORDER BY age desc) 등급

\

[]{}

FROM EMP2;

\

Pb 141. 위에 결과에서 등급이 1등급이 학생들만 출력하시오 SELECT \*

FROM(

SELECT telecom, ename,age,

NTILE(4) OVER (PARTITION BY telecom ORDER BY age desc) 등급 FROM EMP2

)

WHERE 등급=1;

\

[]{}

\

[Accumulating data]{#bookmark68}

ex)

select empno, ename, sal,

o[ ]{.s12}[sum(Sal) over (order by empno) 누적치 from emp;]{.p}

\

[]{}

Pb 142. 부서번호, 사원번호, 이름, 월급, 월급의 누적치를 출력하는데
월급의 누적치가

부서번호별로 각각 월급의 누적치가 출력되게 하시오 SELECT deptno, empno,
ename, sal,

SUM(sal) OVER (PARTITION BY deptno ORDER BY sal) 누적치 FROM EMP;

[]{}

\

[listagg function]{#bookmark69}

print data horizontally ex)

select deptno,

o[ ]{.s12}[listagg(ename,’,’) within group (order by ename asc) from
emp]{.p}

group by deptno;

!! group by phrase

\

Pb 143. 통신사, 이름을 출력하는데 통신사 별로 각각 이름이 가로로
출력되게 하시오.

SELECT telecom,

listagg(ename,',') within GROUP(ORDER BY telecom asc) fROM EMP2

[]{}

GROUP BY telecom;

\

Pb 144. 아래와 같이 결과를 출력하시오. SELECT telecom,

listagg(ename || '(' || age || ')',',') within GROUP(ORDER BY age desc)
FROM EMP2

GROUP BY telecom;

\

[]{}

\

[lead, lag function]{#bookmark70}

“print out previous or next row on next line” ex)

select empno, ename, sal,

lead(sal, 1) over (order by empno) lead\_sal, lag(sal,1) over (order by
empno) lag\_sal from emp;

\

[]{}

\

Pb145. 이름, 생일, 나의 바로 전 생일자 생일, 나의 바로 다음생일자 생일

SELECT ename,age,birth,

LEAD(age,1) OVER( ORDER BY age) lead\_birth, lag(age,1) OVER( ORDER BY
age) lag\_birth FROM EMP2

[]{}

ORDER BY age DESC;

\

Pb 146. 부서번호, 사원번호, 이름, 월급을 출력하고 그 옆에 부서번호별로
각각 바로 그 전 사원번호인 사원의 월급이 출력되게 하고 부서별로
정렬하시오

SELECT deptno, empno, ename, sal,

LEAD(sal,1) OVER(PARTITION BY deptno ORDER BY sal asc) lead\_sal,
lag(sal,1) OVER(PARTITION BY deptno ORDER BY sal asc) lag\_sal FROM EMP

ORDER BY deptno ASC;

\

[pivot review]{#bookmark71}

// row→col ex)

select \*

from (select deptno, sal from emp) pivot( sum(Sal) for deptno in
(10,20,30))

\

[unpivot review]{#bookmark72}

// col → row

\

예제)

SELECT \* FROM order2

unpivot ( cnt FOR item IN (BICYCLE,CAMERA,NOTEBOOK));

// item, cnt ← any name is okay

Pb 147. 살인이 가장 많이 일어나는 장소가 어디인가 SELECT
crime\_type,c\_loc,cnt,

RANK() OVER (ORDER BY cnt desc) 순위 FROM(

SELECT \*

from crime\_loc

unpivot(cnt for c\_loc in( 아파트, 집, 고속도로, 노상, 상점, 시장노점,
숙박업소, 병원, 사무실, 공장, 공사장, 창고, 역대합실, 지하철, 교통,
유흥접객업소, 유원지, 학교, 금융기관, 의료기관, 종교기관, 산야,해상,
부대, 구금장소, 공지, 기타 ))

)

WHERE crime\_type='살인' ORDER BY cnt DESC;

\

[]{}

\

Pb 148. 절도가 많이 일어나는 장소가 어디인지 장소와,건수와 순위가 출력
SELECT crime\_type,c\_loc,cnt,

RANK() OVER (ORDER BY cnt desc) 순위 FROM(

SELECT \*

from crime\_loc

unpivot(cnt for c\_loc in( 아파트, 집, 고속도로, 노상, 상점, 시장노점,
숙박업소, 병원, 사무실, 공장, 공사장, 창고, 역대합실, 지하철, 교통,
유흥접객업소, 유원지, 학교, 금융기관, 의료기관, 종교기관, 산야,해상,
부대, 구금장소, 공지, 기타 ))

)

WHERE crime\_type='절도'

\

ORDER BY cnt DESC;

\

[]{}

Pb 149. 살인을 일으키는 가장 큰 원인이 무엇인지 범죄 원인, 건수, 순위를
출력하시오 !

SELECT crime\_type,c\_loc, cnt,

RANK() OVER (ORDER BY cnt desc) rank FROM crime\_cause

unpivot(cnt FOR c\_loc IN ( 생계형,

유흥,

도막, 허영심, 복수,

해고,

징벌, 가정불화, 호기심, 유혹,

사고,

불만, 부주의, 기타))

WHERE crime\_type='살인';

\

[]{}

Pb150.

create table crime\_cause2 as

SELECT crime\_type, cause, cnt,

RANK() OVER (ORDER BY cnt desc) rank FROM crime\_cause

unpivot(cnt FOR cause IN ( 생계형,

유흥,

도막, 허영심, 복수,

해고,

징벌, 가정불화, 호기심, 유혹,

사고,

불만, 부주의, 기타))

WHERE crime\_type='살인';

You can make table by bring the result, and then query again Pb 151.
가정불화로 인해서 생기는 범죄유형을 출력하시오.

SELECT crime\_type,

\

RANK() OVER (ORDER BY cnt desc) 순위

[]{}

FROM crime\_cause2 WHERE cause='가정불화';

\

Pb 152. 방화 원인 순위1개 1개만 출력하시오. SELECT cause

FROM(

SELECT cause, cnt,

RANK() OVER (ORDER BY cnt desc) 순위 FROM crime\_cause2

WHERE crime\_type='방화'

)

WHERE 순위=1;

\

[]{}

o[ ]{.s12}[서울시 물가 데이터를 오라클에 입력]{.p}

&gt;ed price.sql

// put query

&gt;@price.sql Pb 153.

select \* from price;

Pb 154. 사과를 파는 판매장과 가격을 출력하는데 가격이 높은곳부터 SELECT
a\_name,a\_price,m\_name

FROM price

WHERE a\_name LIKE '%사과%' ORDER BY a\_price DESC;

\

[]{}

Pb 155. 위에 결과를 다시 출력하는데 가격의 순위도 같이 출력하시오

SELECT a\_name,a\_price,m\_name,

DENSE\_RANK() OVER (ORDER BY a\_price desc) AS 순위 FROM price

[]{}

WHERE a\_name LIKE '%사과%' ORDER BY a\_price desc;

\

Pb 156. 위의 결과에서 순위가 1위부터 10까지 출력 SELECT \*

FROM (

SELECT a\_name,a\_price,m\_name,

DENSE\_RANK() OVER (ORDER BY a\_price desc) AS 순위 FROM price

WHERE a\_name LIKE '%사과%' ORDER BY a\_price DESC

)

WHERE 순위 BETWEEN 1 AND 10;

\

[]{}

\

[Excel date to oracle database]{#bookmark73}

sqlgate → import → csv → …

Pb 157. 마지막문제 SELECT cname FROM(

SELECT cname, Y2012

FROM sucide

ORDER BY Y2012 DESC NULLS LAST

)

WHERE rownum=1;

\

SELECT cname FROM(

SELECT cname,

DENSE\_RANK() OVER (ORDER BY Y2012 DESC NULLs last) 순위

FROM sucide

)

where 순위=1;

\

[]{}

\

Pb 158. 직업, 이름, 입사일, 순위를 출력하는데 순위가 직업별로 각각 먼저
입사한 사원순으로 순위를 출력하시오!

\

SELECT job,ename,hiredate,

[]{}

DENSE\_RANK() OVER (PARTITION BY job ORDER BY hiredate asc) 순위 FROM
EMP;

\

Pb 159. 위의 결과에서 1등만.

\

[]{}

\

[Chapter 6. Join]{#bookmark74}

여러개의 테이블의 데이터를 하나의 결과로 모아서 출력하는 SQL 문법

\

[Join list]{#bookmark75}

[oracle join]{#bookmark76}

\

-   equi join

-   non equi join

-   outer join

-   self join

    [1999 ANSI join]{#bookmark77}

    -   full outer join

    -   right outer join

    -   left outer join

    -   on clause join

    -   using clause join

    -   natural join

    -   cross join

\

ex) select \* from dept;

\

[]{}

\

[Equi join]{#bookmark78}

ex) 이름과 부서위치를 출력하시오!

select ename, loc from emp, dept

where emp.deptno = dept.deptno; // join query, not search query.

\

[]{}

ex)

select ename, loc from emp, DEPT;

\

[]{}

Pb 160) 사원번호, 이름, 월급, 부서위치를 출력하시오!

-   SELECT empno,ename,sal,loc

-   FROM emp, DEPT

-   WHERE emp.deptno=dept.deptno;

    \

    []{}

    Pb 161. 사원번호, 이름, 월급, 부서위치, 부서번호를 출력하시오!

-   SELECT emp.deptno,empno,ename,sal,loc

-   FROM emp, DEPT

-   WHERE emp.deptno=dept.deptno;

    \

    []{}

    [Explicit statement for performance]{#bookmark79}

-   SELECT emp.deptno, emp.empno, emnp.ename, emp.sal, dept.loc

-   FROM emp, DEPT

-   WHERE emp.deptno=dept.deptno;

-   SELECT e.deptno, e.empno, e.ename, e.sal, d.loc

-   FROM emp e, DEPT d

-   WHERE e.deptno=d.deptno;

    \

    Pb 162. 월급이 3000이상인 사원들의 이름과 월급과 부서위치를
    출력하시오!

-   SELECT E.eNAME, e.sal, e.deptno

-   FROM EMP e, DEPT d

-   WHERE e.deptno=d.deptno AND e.sal &gt;=3000;

    \

    []{}

    Pb 163. 이름의 첫글자가 S로 시작하는 사원들의 이름과 부서위치를
    출력하시오!

-   SELECT E.eNAME, e.deptno

-   FROM EMP e, DEPT d

-   WHERE e.deptno=d.deptno AND e.ename LIKE 'S%';

    \

    []{}

    Pb 164. 월급이 1000과 3000 사이 출력.

-   SELECT E.eNAME, e.sal, e.deptno, d.dname

-   FROM EMP e, DEPT d

-   WHERE e.deptno=d.deptno AND e.sal BETWEEN 1000 AND 3000;

    \

    []{}

    Pb 165. DALLAS 근무

-   SELECT E.eNAME, d.loc

-   FROM EMP e, DEPT d

-   WHERE e.deptno=d.deptno AND d.loc='DALLAS';

    \

    []{}

    Pb. 166.

-   SELECT d.loc, listagg(E.eNAME,',') within GROUP (ORDER BY E.eNAME)

-   FROM EMP e, DEPT d

-   WHERE e.deptno=d.deptno

    []{}

-   GROUP BY d.loc;

    \

    Pb 167. 부서위치, 이름 월급,순위를 출력하는데 순위가 부서위치별로
    각각 워급이 높은순서대로 순위출력

-   SELECT d.loc,e.ename, e.sal, DENSE\_RANK() OVER(PARTITION BY d.loc
    ORDER BY e.sal desc) 순위

-   FROM EMP e, DEPT d

    []{}

-   WHERE e.deptno=d.deptno

    \

    DROP TABLE salgrade; create table salgrade ( grade number(10), losal
    number(10), hisal number(10) );

    insert into salgrade values(1,700,1200); insert into salgrade
    values(2,1201,1400); insert into salgrade values(3,1401,2000);
    insert into salgrade values(4,2001,3000); insert into salgrade
    values(5,3001,9999);

    \

    commit;

    \

    [Non equi join]{#bookmark80}

    SELECT e.ename, s.grade FROM EMP e,salgrade s

    WHERE e.sal BETWEEN s.losal AND s.hisal

    \

    [Daemon process]{#bookmark81}

    → optimizer

    SQL문의 실행계획을 만들고 실행을 한다 Pb 168. 등급 5만 출력

    SELECT e.ename, s.grade FROM EMP e,salgrade s

    WHERE e.sal BETWEEN s.losal AND s.hisal AND s.grade=5;

    Pb 169. print out like the below

-   SELECT s.grade,listagg(e.ename,',') WITHin GROUP(ORDER BY s.grade
    desc) grade

-   FROM EMP e, salgrade s

-   WHERE e.sal BETWEEN s.losal AND s.hisal

-   GROUP BY s.grade;

    \

    []{}

    \

    Pb 170. 아래와 같이 결과를 출력

-   SELECT s.grade,listagg(e.ename || '(' || e.sal || ')' ,',') WITHin
    GROUP(ORDER BY s.grade desc) grade

-   FROM EMP e,salgrade s

-   WHERE e.sal BETWEEN s.losal AND s.hisal

    []{}

-   GROUP BY s.grade;

    \

    Pb 171.

    \

-   SELECT s.grade, listagg(e.ename || '(' ||
    LTRIM(TO\_CHAR(e.sal,'9,999')) || ')' ,', ')

    WITHin GROUP(ORDER BY s.grade desc) grade

-   FROM EMP e,salgrade s

-   WHERE e.sal BETWEEN s.losal AND s.hisal

-   GROUP BY s.grade;

    \

    []{}

    \

    Pb 172. 이름과 월급과 등급 출력 SELECT e.ename, s.grade, e.sal FROM
    EMP e,salgrade s

    WHERE e.sal BETWEEN s.losal AND s.hisal; Pb 173. 아래와 같이 결과를
    출력

-   SELECT e.ename,

     [DECODE(s.grade,5,'A',4,'B',3,'C',2,'D',1,'F'),]{.p}

-   e.sal

-   FROM EMP e,salgrade s

-   WHERE e.sal BETWEEN s.losal AND s.hisal;

    \

    []{}

    Pb 174.

    SELECT grade,listagg(ename,',') within GROUP (ORDER BY ename desc)
    from

    (

    SELECT e.ename, DECODE(s.grade,5,'A',4,'B',3,'C',2,'D',1,'F') AS
    grade

    \

    FROM EMP e,salgrade s

    WHERE e.sal BETWEEN s.losal AND s.hisal

    )

    GROUP BY grade;

    \

    []{}

    \

    [Outer join]{#bookmark82}

     [equi join 으로는 볼수 없는 결과를 볼때 사용하는 조인으로 equi
    join 으로 조인 안된 데이터를 볼때 사용하는 방법]{.p}

-   Select e.ename, d.loc

-   FROM DEPT d,EMP e

    []{}

-   WHERE e.deptno (+) = d.DEPTNO;

    \

    Pb 175. 아래의 데이터를 입력하고 사원이름은 있고 부서위치가 null인
    겨로가를 출력되게 하시오

-   select e.ename,d.loc

-   FROM DEPT d,EMP e

-   WHERE e.deptno = d.DEPTNO (+);

    \

    []{}

    Pb 176. 아래와같이

-   select e.ename,d.loc

-   FROM EMP e FULL outer JOIN DEPT d

-   on e.deptno = d.DEPTNO;

    \

    []{}

    query&gt;

    DELETE FROM EMP where hiredate IS NULL; COMMIT;

    \

    [self join]{#bookmark83}

    “자기 자신의 테이블과 조인하는 문법”

    177\. 사원이름, 관리자의 이름을 출력하시오! (직속상사) SELECT e.ename,
    m.ename

    \

    FROM EMP m , EMP e

    WHERE m.mgr=e.empno; 178. 아래와 같이

    SELECT e.ename AS 관리자, m.ename AS 직원 FROM EMP m , EMP e

    WHERE e.empno(+) = m.mgr;

    \

    []{}

    179\. 아래와 같이

-   SELECT e.ename ,listagg(m.ename,',') within GROUP (ORDER BY e.ename)
    AS Employee

-   FROM EMP m , EMP e

-   WHERE e.empno(+) = m.mgr

    []{}

-   GROUP BY e.ename;

    \

    180\. 부서위치, 이름, 월급, 순위를 출력하는데 순위가 부서위치별로 각각
    월급이 높은 사원순으로 순위를 부여하시오!

-   SELECT d.loc,e.ename,e.sal,

-   DENSE\_RANK() OVER (PARTITION BY loc ORDER BY sal) AS 순위

-   FROM EMP e, DEPT d

-   WHERE e.deptno=d.deptno; Pb 181. 통신사 테이블 생성한다.

    \

-   create table telecom\_price (

-   telecom varchar2(10),

-   t\_price number(10),

-   t\_profit number(10));

-   insert into telecom price

     [values(‘sk’,60000,0);]{.p}

-   insert into telecom\_price

     [values(‘lg’,65000,3);]{.p}

-   insert into telecom\_price

     [values(‘kt’,64000,2);]{.p}

-   commit; 182.

    SELECT e.ename, e.age, e.telecom, t.t\_price FROM EMP2 e,
    telecom\_price t

    WHERE e.telecom=t.telecom;

    \

    []{}

    Pb 183.

    SELECT d.loc,SUM(e.sal) FROM EMP e, DEPT d

    []{}

    WHERE e.deptno=d.deptno GROUP BY d.loc;

    \

    pb 184. 통신사별 금액 합 출력 SELECT t.telecom, SUM(t.t\_price) FROM
    EMP2 e, telecom\_price t WHERE e.telecom=t.telecom

    \

    []{}

    GROUP BY t.telecom;

    \

    Pb 185. 이름,나이, 통신사, 통신사 월납정액을 출력하는데 CJH를 쓰는
    이근호 학생이 출력되게 하시오!

    SELECT e.ename, e.age, t.telecom, t.t\_price FROM EMP2 e,
    telecom\_price t

    WHERE e.telecom=t.telecom (+);

    SELECT \* FROM SUCIDE;

    \

    []{}

    \

    [right/left outer join (264p \~ 265p)]{#bookmark84}

    “SQL of outer join of oracle join, expressed by 1999 ansi.”

-   oracle join

    ex) select e.ename , dloc from emp e, dept d

    where e.deptno (+) = d.deptno;

-   1999 ansi join select e.ename, d.loc

    from emp e right outer join dept d on ( e.deptno= d.deptno)

    !! oracle join use search condition in where clause, but ansi join
    only use join caluse in

    ‘on’ caluse.

    Pb 186. change the below oracle join query to 1999 ansi query.

-   SELECT e.ename, d.loc

-   FROM EMP e left outer JOIN DEPT d

-   ON (e.deptno=d.deptno);

    \

    Pb 187. emp2 와 telecom\_price 를 조인해서 아래의 결과를 출력하시데
    1999 ansi 문법으로 수행하시오.

-   SELECT e.ename, t.t\_price

    \

-   FROM EMP2 e left outer JOIN TELECOM\_price t

-   ON (e.telecom = t.telecom)

    \

    []{}

    \

    [on Join]{#bookmark85}

    “join query in “on clause”

-   oracle join query select e.ename, d.loc from emp e, dept d

    where e.deptno=d.deptno;

-   1999 ansi join query select e.ename, d.loc from emp e join dept d on
    (e.deptno = d.deptno);

    Pb 188. 이름과 통신사 월정앵ㄱ을 출력하는데 on절을 사용한
    조인문법으로 수행하시오

-   SELECT e.ename, t.t\_price

-   FROM EMP2 e JOIN TELECOM\_price t

-   ON (e.telecom = t.telecom)

\

[3 tables join]{#bookmark86}

ex) 이름, 월급, 부서위치, 급여등급(grade)을 출력하시오!

-   oracle join

select e.ename, e.sal, d.loc, s.grade from emp e, dept d, salgrade s

where (e.deptno=d.deptno) and e.sal between s.losal and s.hisal;

The number of join condition = the number of tables-1

Pb 189. 아래에 보너스라는 테이블을 생성하고 이름과 월급과 부서위치와
보너스를 출력하시오!

create table bonus as

\

-   select empno, sal\*30 as bonus

-   from emp;

-   SELECT e.ename, e.sal, d.loc, b.bonus

-   FROM EMP e, DEPT d, bonus b

-   WHERE e.deptno=d.deptno AND e.empno=b.empno

    \

    []{}

    Pb 190. 위의 sql을 on절을 사용한 조인 문법으로 변경하시오! SELECT
    e.ename, e.sal, d.loc, b.bonus

    FROM EMP e JOIN DEPT d

    ON(e.deptno=d.deptno) JOIN bonus b ON(e.empno=b.empno);

    Pb 191. 이름, 월급, 부서위치, 급여등급(grade)을 출력하시오!( on절을
    사용한 조인)

-   SELECT e.ename, e.sal, d.loc, g.grade

-   FROM EMP e JOIN DEPT d

-   ON (e.deptno=d.deptno) JOIN SALGRADE g ON (e.sal BETWEEN g.losal AND
    g.hisal) Pb 192. 이름과 부서위치를 출력하는데 DAALS 근무만.

    -   oracle join

-   SELECT e.ename, d.loc

-   FROM EMP e, DEPT d

-   WHERE e.deptno=d.deptno AND d.loc='DALLAS';

    -   1999 ANSI join

-   SELECT e.ename, d.loc

-   FROM EMP e JOIN DEPT d

-   on e.deptno=d.deptno

-   WHERE d.loc='DALLAS';

    \

    [using join (249p)]{#bookmark87}

    ex) 이름과 부서위치를 using 절을 사용한 조인으로 출력한다.

    select e.ename, d.loc from emp e join dept d

    using(deptno); //do not write like e.deptno

    pb 193. 학생이름, 통신사 월정액을 출력하는데 using 절을 사용한
    조인으로 출력하시오!

-   SELECT e.ename, t.t\_price

-   FROM EMP2 e JOIN TELECOM\_PRICE t

    \

-   USING(telecom);

    \

    [natural join (245 \~246)]{#bookmark88}

    이름과 부서위치를 출력 select e.ename, d.loc

    from emp e natural join dept d;

    // automatically join

    \

    [cross join (p 270)]{#bookmark89}

    “join everything”

-   oracle

-   select e.ename, d.loc

-   from emp e, dept d;

-   1999 ansi

-   select e.ename, d.loc

-   from emp e cross join dept d;

    P 194. 부서위치, 부서위치별 토탈월급, 부서위치별 최대월급,
    부서위치별 최소월급, 부서위치별 인원수를 출력하시오!

-   SELECT d.loc, SUM(e.sal), MAX(e.sal), MIN(e.sal), COUNT(e.empno)

-   FROM EMP e JOIN DEPT d

-   ON e.deptno=d.deptno

-   GROUP BY d.loc;

    Pb 195. 부서위치, 부서위치별 인원수를 출력하는데 부서위치별 인원수가
    3명 이상인것만 출력하고 부서위치별 인원수가 높은것부터 출력하시오!

-   SELECT d.loc, COUNT(\*)

-   FROM EMP e JOIN DEPT d

-   ON e.deptno=d.deptno

-   GROUP BY d.loc

-   HAVING COUNT(\*) &gt;=3

-   ORDER BY COUNT(\*) DESC;

    \

    []{}

    Pb 196.

-   SELECT e.telecom, sum(t.t\_price)

    \

-   FROM EMP2 e JOIN TELECOM\_PRICE t

-   ON e.telecom=t.telecom

-   GROUP BY e.telecom

-   HAVING sum(t.t\_price)&gt;=100000

-   ORDER BY sum(t.t\_price) DESC;

    \

    []{}

    \

    Pb. 197.

    SELECT job,

    SUM(DECODE(d.loc,'DALLAS',e.sal,0)) AS DALLAS,
    SUM(DECODE(d.loc,'CHICAGO',e.sal,0)) AS CHICAGO,
    SUM(DECODE(d.loc,'NEW YORK',e.sal,0)) AS "NEW YORK" FROM EMP e JOIN
    DEPT d

    []{}

    ON e.deptno = d.deptno GROUP BY job;

    \

    SELECT \* FROM

    (

    SELECT e.job,e.sal,d.loc FROM EMP e JOIN DEPT d

    ON e.deptno = d.deptno

    )

    pivot(SUM(sal) FOR loc IN ('DALLAS','CHICAGO','NEW YORK'));

    \

    []{}

    \

    Pb 198.부서위치, 부서위치별 토탈월급을 세로로 출력하시오!

    \

    SELECT d.loc, SUM(e.sal)

    FROM EMP e JOIN DEPT d

    ON e.deptno = d.deptno GROUP BY d.loc;

    \

    []{}

    \

    Pb 199. 부서위치, 부서위치별 토탈월급을 아래와 같이 가로로 출력.

    SELECT \* FROM (

    SELECT d.loc, e.sal

    FROM EMP e JOIN DEPT d

    ON e.deptno = d.deptno

    )

    pivot(SUM(sal) FOR loc IN ('DALLAS','CHICAGO','NEW YORK'));

    \

    []{}

    \

    Pb 200.

    SELECT \* FROM

    (

    SELECT TO\_CHAR(e.hiredate,'RRRR') AS hiredate,e.sal FROM EMP e JOIN
    DEPT d

    ON e.deptno = d.deptno

    )

    pivot(SUM(sal) FOR hiredate IN ('1980','1981','1982','1983'));

    \

    []{}

    Pb 201.

    SELECT \* FROM

    (

    SELECT d.loc,TO\_CHAR(e.hiredate,'RRRR') AS hiredate,e.sal FROM EMP
    e JOIN DEPT d

    \

    ON e.deptno = d.deptno

    )

    pivot(SUM(sal) FOR hiredate IN ('1980','1981','1982','1983'));

    \

    문제 202. 아래와 같이 결과를 출력하시오!

    SELECT \* FROM

    (

    SELECT e.job,d.loc

    FROM EMP e JOIN DEPT d

    ON e.deptno = d.deptno

    )

    pivot(count(\*) FOR loc IN ('DALLAS','CHICAGO','NEW YORK'));

    \

    []{}

    \

    Pb. 203. DALLAS 에서 근무하는 사원들의 월급중 최대월급

-   SELECT MAX(e.sal)

-   FROM EMP e JOIN DEPT d

-   ON e.deptno = d.deptno

-   WHERE d.loc='DALLAS';

    \

    Pb 204. CHICAGO 에서 근무하는 사원들중에 가장 늦게 입사한 사원의
    입사일을 출력

-   SELECT MAX(e.hiredate)

-   FROM EMP e JOIN DEPT d

-   ON e.deptno = d.deptno

-   WHERE d.loc='CHICAGO';

[Chapter 8. set operator]{#bookmark90}

[]{}

\

[list of set operators]{#bookmark91}

set function

-   union all\\

-   union

-   grouping sets

-   roll reporting function [o]{.s11}[ ]{.s12}roll up

-   cube

-   grouping sets

\

[Union]{#bookmark92}[all]{.s6}

“ combine two results and print out into one” ex)

o[ ]{.s12}[직업, 직업별 토탈월급 출력 SELECT job,SUM(Sal)]{.p}

FROM EMP GROUP BY job;

\

[]{}

o[ ]{.s12}[사원테이블의 전체 토탈월급을 출력하시오]{.p}

[]{}

SELECT SUM(Sal) FROM EMP;

\

\* 위의 두개의 결과 집합을 하나의 합집합으로 출력하시오 SELECT
job,SUM(Sal)

FROM EMP GROUP BY job UNION all

SELECT '전체토탈', SUM(Sal)

FROM EMP;

The difference between union and union all Guidelines

The guidelines for UNION and UNION ALL are the same, with the following
two exceptions that pertain to UNION ALL: Unlike UNION, duplicate rows
are not eliminated and the output is not sorted

by default. Pb 205.

SELECT job,TO\_CHAR(SUM(Sal),'99,999') FROM EMP

GROUP BY job UNION all

[]{}

SELECT '전체토탈', TO\_CHAR(SUM(Sal),'99,999') FROM EMP;

\

Pb 206. 아래와 같이 결과를 출력하시오! SELECT TO\_CHAR(deptno), SUM(sal)

\

FROM EMP

GROUP BY deptno UNION ALL

SELECT '전체토탈',SUM(sal) FROM EMP;

[]{}

Pb 207.

-   SELECT job, count(\*)

-   FROM EMP

-   GROUP BY job

-   UNION ALL

-   SELECT '전체토탈',count(\*)

    []{}

-   FROM EMP;

    \

    Pb 208. 부서번호, 부서번호별 평균월급을 출력하는데 맨 아래쪽에 전체
    평균월급을 출력하시오

-   SELECT TO\_CHAR(deptno), ROUND(aVG(sal))

-   FROM EMP

-   GROUP BY deptno

-   UNION ALL

-   SELECT null,ROUND(avg(sal))

    []{}

-   FROM EMP;

    \

    Pb 209. 부서번호, 부서번호별 토탈월급을 출력하는데 아래와 같이 맨
    아래쪽에 전체 토탈월급을 출력하시오!

    -   SELECT TO\_CHAR(deptno), sum(sal)

    -   FROM EMP

    -   GROUP BY deptno

    -   UNION ALL

    -   SELECT null,SUM(sal)

    -   FROM EMP;

        \

        []{}

        \

        [Rollup]{#bookmark93}

    -   SELECT deptno, SUM(sal)

    -   FROM EMP

    -   GROUP BY ROLLUP(deptno);

\

[]{}

Pb. 210

SELECT nvl(job,'전체토탈'), TO\_CHAR(SUM(sal),'99,999') FROM EMP

GROUP BY ROLLUP(job);

\

[]{}

Pb 211. 입사한 년도(4자리), 입사한 년도별 토탈월급을 출력하시오!

-   SELECT (TO\_CHAR(hiredate,'RRRR')), ㅜTO\_CHAR(SUM(sal),'99,999')

-   FROM EMP

-   GROUP BY TO\_CHAR(hiredate,'RRRR');

    Pb 212. 위의 결과에 맨 아래쪽에 전체 토탈월급이 출력되게 하시오

-   SELECT nvl(TO\_CHAR((TO\_CHAR(hiredate,'RRRR'))),'전체토탈'),
    TO\_CHAR(SUM(sal),'99,999')

-   FROM EMP

-   GROUP BY ROLLUP(TO\_CHAR(hiredate,'RRRR'));

    \

    []{}

    Pb213. 부서위치, 부서위치별 토탈월급을 출력

-   SELECT d.loc, SUM(e.sal)

-   FROM EMP e, DEPT d

-   WHERE e.deptno=d.deptno

-   GROUP BY d.loc;

    \

    []{}

    Pb 214. 위의 결과에서 맨 아래쪽에 전체 토탈 월급이 출력되게 하시오

-   SELECT d.loc, SUM(e.sal)

-   FROM EMP e, DEPT d

-   WHERE e.deptno=d.deptno

-   GROUP BY ROLLUP(d.loc);

    \

    []{}

    \

    cube

    Pb 215. 토탈월급이 아래쪽에 출려고디는게 아니라 위쪽에 출력되게
    하시오

-   SELECT d.loc, SUM(e.sal)

-   FROM EMP e, DEPT d

-   WHERE e.deptno=d.deptno

    []{}

-   GROUP BY cube(d.loc);

\

Pb 216. 위의 결과를 다시 출력하는데 이번에는 cube쓰지말고 union all로
수행해 보시오 !

\

SELECT null, SUM(e.sal)

FROM EMP e, DEPT d

WHERE e.deptno=d.deptno UNION all

SELECT d.loc, SUM(e.sal) FROM EMP e, DEPT d

WHERE e.deptno=d.deptno GROUP BY d.loc;

[]{}

\

Union

eliminate duplicated rows

\

ex)

select deptno from emp union all select deptno from emp;

\

[]{}

vs

seelct deptno from emp union

select deptno from emp;

\

[]{}

not only eliminate duplication but also sort.

Pb 216. 아래의 SQL의 결과와 똑같은 결과가 나오게끔 union all로
작성해보시오 select deptno,SUM(sal)

from EMP

GROUP BY deptno UNION

select NULL, SUM(sal) from emp;

\

select deptno,SUM(sal) from EMP

GROUP BY deptno UNION all

select NULL as deptno, SUM(sal)

from emp

ORDER BY deptno ASC;

\

[]{}

\

[order by should be last]{#bookmark94}

Pb217. 아래의 sql의 결과를 union all로 수행하시오

select deptno, sum(Sal) from emp

group by cube(deptno);

\`select NULL AS deptno, sum(Sal)\` from emp

UNION all

select deptno,sum(Sal) from emp

\

GROUP BY deptno

ORDER BY deptno asc nulls first;

\

[]{}

\

[Reporting function list]{#bookmark95}

1.  rollup

2.  cube

3.  grouping sets

4.  grouping

[Roll up]{#bookmark96}

Pb 218. 직업, 부서번호, 직업별 부서번호별, 토탈월급을 출력하시오. SELECT
deptno,job, SUM(sal)

FROM EMP

GROUP by deptno,job ORDER BY deptno, job;

[]{}

Example

pb219. 아래와 같이 출력하시오

-   SELECT deptno,job, SUM(sal)

-   FROM EMP

-   GROUP by ROLLUP((deptno,job));

\

[]{}

SELECT deptno,job, SUM(sal)

FROM EMP

GROUP by ROLLUP(deptno,job);

\

[]{}

\

Pb220. 텔레콤, 전공, 텔레콤별 전공별 인원수를 출력하시오. SELECT
telecom,major,COUNT(\*)

FROM EMP2

GROUP BY telecom,major;

\

Pb 221. 위의 결과에서 맨 아래쪽에 전체토탈 인원수가 출력되게 하시오.
SELECT telecom,major,COUNT(\*)

FROM EMP2

GROUP BY ROLLUP((telecom,major));

\

Pb 222. 위의 결과를 아래와 같이 중간중간 통신사별 인원수도 출력되게
하시오 SELECT telecom,major,COUNT(\*)

FROM EMP2

GROUP BY ROLLUP(telecom,major);

\

[Grouping sets]{#bookmark97}

ex)

Pb 222를 rollup이 아니라 grouping sets로 변경해보세요 select telecom,
major, count(\*)

from emp2

group by grouping sets( (telecom,major),

(major),

());

\

PB 223. 아래의 rollup의 결과를 grouping sets로 수행하시오! SELECT
deptno, SUM(sal)

FROM EMP

GROUP BY ROLLUP(deptno);

select deptno, SUM(sal) from emp

group by grouping sets( (deptno),

());

\

Pb 224. 아래의 rollup의 결과를 grouping sets 로 변경하시오 select
deptno, job, sum(sal)

from emp

group by rollup(deptno,job); select deptno, job, sum(sal) from emp

group by GROUPING sets ((deptno,job), (deptno),());

\

Pb 225.

아래와 같이 결과를 출력하시오

select deptno, NVL(job,'부서토탈'), sum(sal) from emp

group by GROUPING sets ((deptno,job), (deptno)); Pb 226.

select deptno,

\

CASE WHEN deptno IS NULL THEN '전체토탈'

else NVL(job,'부서토탈') END,

sum(sal) from emp

group by GROUPING sets ((deptno,job), (deptno),());

select deptno, DECODE(deptno,NULL,'전체토탈',NVL(job,'부서토탈')),
sum(sal)

from emp

group by GROUPING sets ((deptno,job), (deptno),());

\

[]{}

\

Pb 227. 아래와 같이 결과를 출력하시오!

-   SELECT DEPTno,ename,SUM(sal)

-   FROM EMP

-   GROUP BY GROUPING sets((ename,deptno),())

-   ORDER BY deptno;

    \

    []{}

    \

    문제 228. 위의 결과를 grouping sets를 쓰지 말고 uinon all로 해서
    수행하시오

-   SELECT deptno,ename,SUM(sal)

-   FROM EMP

-   GROUP BY GROUPING sets((deptno,ename))

-   UNION ALL

-   SELECT NULL,null,SUM(sal)

-   FROM EMP

-   ORDER BY deptno;

\

[]{}

\

Pb 229.

SELECT NVL(job,'토탈값'), SUM(DECODE(deptno,10,sal,0)) "10",

\

SUM(DECODE(deptno,20,sal,0)) "20",

SUM(DECODE(deptno,30,sal,0)) "30" FROM EMP

group BY ROLLUP(job);

\

[]{}

\

Pb 230.

SELECT NVL(TO\_CHAR(age),'전체'),

sum(DECODE(telecom,'sk',1,0)) "SK",

sum(DECODE(telecom,'kt',1,0)) "KT",

sum(DECODE(telecom,'lg',1,0)) "LG",

sum(DECODE(telecom,'chj',1,0)) "CHJ" FROM EMP2

GROUP BY ROLLUP(age);

\

[]{}

SELECT NVL(TO\_CHAR(age) , '토탈') age, SUM(sk),SUM(kt),SUM(lg),SUM(cjh)
FROM (

SELECT age, telecom FROM EMP2

)

pivot (COUNT(\*) FOR telecom IN

('sk' AS sk ,'kt' AS kt,'lg' AS lg,'cjh' AS cjh)) GROUP BY GROUPING sets
((age) ,());

SELECT NVL(TO\_CHAR(age),'전체'),

sum(DECODE(telecom,'sk',1,0)) "SK",

sum(DECODE(telecom,'kt',1,0)) "KT",

\

sum(DECODE(telecom,'lg',1,0)) "LG",

sum(DECODE(telecom,'chj',1,0)) "CHJ" FROM EMP2

GROUP BY ROLLUP(age);

\

Pb 231.아래와 같이 결과를 출력하시오! SELECT NVL(TO\_CHAR(age),'전체'),

sum(DECODE(telecom,'sk',1,0)) "SK",

sum(DECODE(telecom,'kt',1,0)) "KT",

sum(DECODE(telecom,'lg',1,0)) "LG",

sum(DECODE(telecom,'chj',1,0)) "CHJ", COUNT(age) as토탈

FROM EMP2

GROUP BY ROLLUP(age);

\

[]{}

\

[Intersect(321p)]{#bookmark98}

ex) 학생이름이 2건이 입력된 학생을 출력하시오!

-   SELECT ename,COUNT(\*)

-   FROM EMP2

-   GROUP BY ename

-   HAVING COUNT(\*)&gt;=2;

-   delete \* from emp2 where ename=”송윤호”;

-   DELETE FROM EMP2

-   WHERE ROWID = (SELECT ROWID FROM EMP2 WHERE ename='송윤호' AND

    rownum=1);

    o[ ]{.s12}[우리반에 전공이 경제학인 학생들의 데이터만 가지고
    emp7이라는 테이블을 생성하시오!]{.p}

    CREATE TABLE emp7

    \

    AS

    SELECT \* FROM EMP2

    WHERE major = '경제학'; COMMIT;

    Example

    SELECT \* FROM EMP2

    intersect

    SELECT \* FROM emp7;

    \

    []{}

    \

    [minus(324p)]{#bookmark99}

    ex) emp2와 emp7과의 차집합을 출력하시오!

    \

    [Data types according to data size]{#bookmark100}

    1.  small data {#small-data style="display: inline;"}
        ----------

    2.  big data {#big-data style="display: inline;"}
        --------

    to analyze small data

    Server for development ----- Server

    o[ ]{.s12}[100 million -------- 10000milion]{.p}

-   make db link to see emp2 table of ‘Hyechan’

-   create database LINK dblink7

-   CONNECT TO scott

-   IDENTIFIED BY tiger

o[ ]{.s12}[USING '192.168.19.3:1521/xe';]{.p}

Pb 232.짝꿍하고 나하고 emp2 테이블의 데이터의 차이가 존재하는지 확인
SELECT \* FROM EMP2

minus

SELECT \* FROM emp2@dblink7

\

[caution]{#bookmark101}

o[ ]{.s12}[order by 절은 맨 아래쪽 쿼리에만 사용할 수 있고 order by 절을
사용하려면 쿼리문들의 컬럼명이 다 동일해야 한다.]{.p}

o[ ]{.s12}[데이터 타입도 맞춰줘야 한다. ex)]{.p}

-   SELECT deptno, SUM(sal)

-   FROM EMP

-   GROUP BY deptno

-   UNION ALL

-   select TO\_NUMBER(NULL) AS deptno, sum(sal)

-   FROM EMP

-   ORDER BY deptno desc nulls FIRST;

    \

    [grouping]{#bookmark102}

    “null 과 grouping 되는 결과를 보기위해서 어쩔수 업이 null로 출력되는
    데이터를

    구분해 주기 위해서 사용하는 함수 ex)

-   SELECT deptno, SUM(sal),GROUPING(deptno)

-   FROM EMP

-   GROUP BY ROLLUP(deptno);

    \

    []{}

-   UPDATE EMP

-   SET deptno=NULL

-   WHERE deptno=10;

-   SELECT deptno, SUM(sal),GROUPING(deptno)

-   FROM EMP

    []{}

-   GROUP BY ROLLUP(deptno);

\

-------------------------------------------- {#section style="padding-left: 5pt;text-indent: 0pt;text-align: left;"}
============================================

[Subquery in where clause]{#bookmark103}

ex) print out names and salaries of those who have more salary than
JONES.

-   SELECT ename,sal

-   FROM EMP

-   WHERE sal &gt; (SELECT sal FROM EMP WHERE ename='JONES')

    \

    []{}

    Pb 233. SCOTT 과 같은 월급을 받는 사원의 이름과 월급을 출력하시오!

-   SELECT ename,sal

-   FROM EMP

    []{}

-   WHERE sal = (SELECT sal FROM EMP WHERE ename='SCOTT');

\

Pb 234. scott 제외 SELECT ename,sal FROM EMP

WHERE sal = (SELECT sal FROM EMP WHERE ename='SCOTT') AND
ename!='SCOTT';

Pb 235. ALLEN 보다 늦게 입사한 사원들의 이름과 입사일을 출력하시오

SELECT ename,hiredate FROM EMP

WHERE hiredate &gt; (SELECT hiredate FROM EMP WHERE ename='ALLEN'); Pb
236. 최대 월급을 받는 사람의 이름과 월급

SELECT ename,sal FROM EMP

WHERE sal = (SELECT MAX(sal) FROM emp);

Pb 237. 가장 어린 학생 이름 나이 SELECT ename, age

FROM EMP2

WHERE age = (SELECT MIN(age) FROM emp2);

\

[university data]{#bookmark104}

input

university tuition fee data

[Table name change]{#bookmark105}

RENAME university\_tuition TO univ;

\

Pb 238. 최대 등록금 대학 SELECT university,tuition FROM
university\_tuition

WHERE tuition = (SELECT MAX(tuition) FROM university\_tuition);

\

Pb 239. 최소 등록금 대학 SELECT university,tuition FROM univ

WHERE tuition = (SELECT MIN(tuition) FROM univ WHERE tuition

!=0);

\

Pb 241. 전국에서 가장 비싼 생필품 이름과 가격과 파는곳을 출력하시오
SELECT a\_name,a\_price,m\_name

FROM PRICE

WHERE a\_price=(SELECT MAX(a\_price) FROM price);

\

[bringing table from other database]{#bookmark106}

create table price as

select \* from sys.price

\

Pb 242. 사랑의 가장 큰 원인 출력(기타제외) SELECT cause

FROM CRIME\_CAUSE2

WHERE cnt = (SELECT MAX(cnt)

FROM CRIME\_CAUSE2 WHERE crime\_type='살인' AND cause!='기타') AND
crime\_type='살인';

\

Pb 243. 가정불화로 인해 생기는 가장 큰 범죄 출력 SELECT crime\_type

FROM CRIME\_CAUSE2

WHERE cause='가정불화' AND cnt=(

\

SELECT MAX(cnt)

FROM CRIME\_CAUSE2

WHERE cause='가정불화'

);

\

Pb 244. JONES 와 직업이 같은 사원들의 이름과 직업을 출력하시오 SELECT
ename,job

FROM EMP

WHERE job=(SELECT job FROM EMP WHERE ename='JONES');

\

[]{}

P 245. JONES는 제외하고 출력 SELECT ename,job

FROM EMP

WHERE job=(SELECT job FROM EMP WHERE ename='JONES') AND ename!='JONES';

\

P 246. 직업이 salesman과 같은 사람의 이름 직업 월급을 출력 SELECT
ename,job,sal

FROM EMP

WHERE sal IN ( SELECT DISTINCT sal FROM EMP WHERE job='SALESMAN');

\

[subquery 3 tyeps]{#bookmark107}

1.  single row subquery

2.  mulitple row subquery

3.  multiple column subquery

    \

    P 247. 전공이 경제학과인 학생들과 통신사가 같은 학생들의 이름과
    전공과 통신사를 출력하시오

    SELECT ename,major,telecom FROM EMP2

    WHERE telecom IN( SELECT telecom FROM EMP2 WHERE major LIKE
    '%경제%');

    \

    P 248. 위의 결과에서 경제학과 제외

    \

    SELECT ename,major,telecom

    FROM EMP2

    WHERE telecom IN( SELECT telecom FROM EMP2 WHERE major LIKE
    '%경제%') AND major NOT LIKE '%경제%';

    \

    P 249. DALLAS 에 있는 부서번호에서 근무하는 사원들의 이름과 월급을
    출력하시오 SELECT ename, sal

    FROM EMP

    WHERE deptno in ( SELECT deptno FROM DEPT

    WHERE loc='DALLAS'

    );

    \

    P 250. King 에게 보고하는 사원들의 이름과 월급을 출력하시오! SELECT
    ename,sal

    FROM EMP

    WHERE mgr = (SELECT empno FROM EMP WHERE ename='KING');

    \

    []{}

    \

    [Single row sub query operators]{#bookmark108}

    = , &lt;&gt;, !=, \^=, &gt;, &lt;, &gt;= , &lt;=

    \

    Single row sub query operators

    in, not in, &gt;all, &lt;all, &gt;any, &lt;any

    \

    P 251. SCOTT과 직업이 같지 않은 사원들의 이름과 직업을 출력하시오.
    SELECT ename,job

    FROM EMP

    WHERE job != (SELECT job FROM EMP WHERE ename='SCOTT');

    \

    P 252. 직업이 SALESMAN 인 사원들과 월급이 같지 않은 사원들의 이름과
    월급과 직업을 출력하시오

    SELECT ename, sal, job

    \

    FROM EMP

    WHERE sal NOT IN (

    SELECT sal FROM EMP

    WHERE job='SALESMAN'

    );

    \

    P 253,254. MGR만 출력(중복, 중복제거) SELECT DISTINCT mgr

    FROM EMP;

    P255. 관리자인 사원들의 이름과 월급을 출력 SELECT ename, sal

    FROM EMP

    WHERE empno IN( SELECT DISTINCT mgr FROM EMP

    );

    \

    P 256. 관리자가 아닌 사원출력 SELECT ename, sal

    FROM EMP

    WHERE empno not IN( SELECT mgr

    FROM EMP

    WHERE mgr IS NOT NULL

    );

    \

    [Beware of sub query - not in (null)]{#bookmark109}

    P 257. [직업이 SALESMAN 인 사원들과 월급이 같고 커미션도 같은
    사원들의 이름과 월급과 직업을 출력]{.p}

    SELECT ename, job, sal FROM EMP

    WHERE sal in (

    SELECT sal FROM EMP

    WHERE job='SALESMAN'

    )

    AND COMM in(

    SELECT comm FROM EMP

    WHERE job='SALESMAN'

    )

    ;

    \

    [Non]{#bookmark110}[pair wise]{.s5}

    P258. [통계학과인 학생들과 통신사도 같고 나이도 같은 학생들의 이름과
    나이와 통신사와 전공 출력]{.p}

    SELECT ename,age,telecom,major FROM EMP2

    WHERE telecom IN ( SELECT telecom

    FROM EMP2

    WHERE major LIKE '%[통계]{.p}%'

    ) AND

    age IN ( SELECT age FROM EMP2

    WHERE major LIKE '%[통계]{.p}%'

    )

    ;

    \

    Pair wise

    \

    SELECT ename, age, major, telecom FROM EMP2

    WHERE (telecom, age) IN ( SELECT telecom,age

    FROM EMP2

    WHERE major LIKE '[통계]{.p}%')

    ;

    \

    \* [Mssql does not support pairwise method!]{.s8}

    \

    가격

    \

    Oracle Mysql Mssql Postre SQL

    Hadoop -hive SQL

    \

    Pb 260. [직업, 이름, 입사일, 순위를 출력하는데 각 직업별로 가장 먼저
    입사한 사원들만]{.p}

    출력하시오 [SELECT \* FROM (]{.s8}

    SELECT job,ename,TO\_CHAR(hiredate,'RR/MM/DD') AS hiredate, RANK ()
    OVER (PARTITION BY job ORDER BY hiredate asc) [순위]{.p}

    FROM EMP

    )

    WHERE [순위]{.p}=1;

    \

    Multiple row subquery operators &gt;all, &lt;all, &gt; any, &lt;any

    P 260. [직업이 SALESMAN 인 사원들의 최대월급보다 더 많은 월급을 받는
    사원들의 이름과 월급을 출력하시오]{.p}

    SELECT ename,sal FROM EMP WHERE sal &gt; (

    SELECT MAX(sal) FROM EMP

    WHERE job='SALESMAN'

    )

    ;

    \

    []{}

    \

    []{}

    SELECT ename, sal // main query is first implemented!! FROM EMP

    WHERE sal &gt; ALL(

    SELECT sal FROM EMP

    WHERE job='SALESMAN'

    );

    \

    [// usually not used in terms of performance]{.s15
    style=" background-color: #FF0;"}

    \

    Pb 261. [직업이 SALESMAN 인 사원중에 가장 적은 월급보다 더 많은
    월급을 받는 사원의 이름과 월급을 출력하시오!]{.p}

    SELECT ename,sal FROM EMP WHERE sal &gt; (

    SELECT min(sal) FROM EMP

    WHERE job='SALESMAN'

    )

    ;

    \

    SELECT ename,sal FROM EMP WHERE sal &gt; (

    SELECT (sal) FROM EMP

    WHERE job='SALESMAN'

    )

    ;

    \

    [Exists clause]{#bookmark111}

    "[메인쿼리에 존재하는 데이터가 서브쿼리에도 존재하는지 찾아보는
    SQL"]{.p}

    o[ ]{.s12}[부서테이블을 출력하시오!]{.p}

    \

    -사원 테이블의 부서번호를 조회하는데 부서테이블에는 존재하는데
    사원테이블에 없는 부서번호 확인

    \

    SELECT deptno FROM dept

    WHERE DEPTno NOT IN (

    SELECT deptno FROM EMP

    );

    \

    [But this is so slow]{.s16 style=" background-color: #0F0;"}

    \

    Tuning : Select deptno From dept d Where exists (

    Select 'x' From emp e

    Where e.deptno=d.deptno

    );

    \

    [// ]{.s16 style=" background-color: #0F0;"}[메인쿼리부터 ]{.s17
    style=" background-color: #0F0;"}[수행하면서 ]{.s17
    style=" background-color: #0F0;"}[존재하면 ]{.s17
    style=" background-color: #0F0;"}[바로 ]{.s17
    style=" background-color: #0F0;"}[출력]{.s17
    style=" background-color: #0F0;"}

    \

    P 263. [이번에는 존재하지 않는 부서번호를 출력]{.p}

    Where NOT EXISTS (

    SELECT 'x'

    From emp e

    Where e.deptno=d.deptno

    );

    \

    P 264. TELECOM\_PRICE [테이블의 통신사를 출력하는데 우리반 ]{.p}EMP2
    [에 존재하는 통신사만 출력]{.p}

    SELECT telecom

    FROM TELECOM\_PRICE t WHERE EXISTS (

    SELECT 'x'

    FROM emp2 e

    WHERE e.telecom=t.telecom

    );

    \

    P 264. TELECOM\_PRICE [테이블의 통신사를 출력하는데 우리반 ]{.p}EMP2
    [에 존재하지 않는 통신사만 출력]{.p}

    SELECT telecom

    FROM TELECOM\_PRICE t WHERE NOT EXISTS (

    SELECT 'x'

    FROM emp2 e

    WHERE e.telecom=t.telecom

    );

    \

    [Chapter 9. DML]{#bookmark112}

    Data [조작언어]{.p}

    1.  Insert

    2.  Update

    3.  Delete

    4.  Merge --&gt; implement insert, update and delete together

\

[Insert]{#bookmark113}

Ex)

insert into emp(empno, ename, sal) Values (123,'JACK',4000);

Select \* from emp;

\

Rollback;

//if you want to go back before input P 266. [아래의 data를
입력하시오]{.p}

\

사원번호 3282

사원이름 JANE 월급 4500 입사일 오늘날짜 부서번호 20

\

[Null]{#bookmark114}

\

Explicit input

1.  Null

2.  ''

\

Ex)

Insert into emp(empno, ename, sal) Values(2911, null, 3400);

\

Insert into emp(empno, ename, sal) Values(2911,'', 3400);

\

Insert into emp(empno, ename, sal) Values(2911,' ', 3400);

\

Implicit input

Insert into emp(empno, ename, sal) Values(2911,'aaa',3400)

[// remain values become null]{.s16 style=" background-color: #0F0;"}

\

P268. [샐러리 이름 출력, 이름 null, 공백 제외]{.p}

SELECT ename,sal FROM EMP

WHERE ename IS NOT NULL AND TRIM(ename)!=' ';

\

[Update]{#bookmark115}

Ex) update emp

Set sal=8000

Where ename='SCOTT';

\

이름이 SCOTT인 사원의 월급을 8000으로 변경

\

P 269. [직업이 SALESMAN 인 사원들의 커미션을 500으로 변경하시오]{.p}

UPDATE EMP

SET comm=5000 WHERE job='SALESMAN';

\

P270. [부서번호가 30번인 사원들의 월급을 0으로 변경하시오]{.p}

UPDATE EMP

SET sal=0 WHERE deptno=30;

\

[FLASHBACK]{#bookmark116}

ALTER TABLE EMP ENABLE ROW MOVEMENT;

\

flashback TABLE EMP TO timestamp
to\_timestamp('2018/04/06:15:30:00','RRRR/MM/DD:HH24/MI:SS');

\

[Calculation]{#bookmark117}

Select log(2,64) from dual; Select LN(10) from dual;
