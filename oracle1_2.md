# Restricting and Sorting Data

  1. where 절 사용법
  2. 비교 연산자 사용법
  3. 기타 비교 연산자 사용법
  4. 논리 연산자 사용법
  5. 연산자 우선순위

## where 절 사용법

  “where 절은 데이터 검색조건을 기술하는 절”
  예제)
  	
    select 컬럼
  	from 테이블
  	where 검색조건문


  사원번호가 7788번인 사원의 사원번호와 이름을 출력하시오
  	
    3~ select empno, ename
  	1~ from emp
  	2~ where empno= 7788; (검색조건)
  앞에는 실행순서
  
  문제14. 월급이 3000인 사원의 이름과 월급을 출력하시오
    
    select ename, sal 
    from emp 
    where sal=3000;
  
  문제15. 월급이 1500 이상인 사원들의 이름과 월급을 출력하시오
    
    select ename, sal
    from emp
    where sal >=2500;
  
  문제16. 연봉이 36000이상인 사원들의 이름과 연봉을 출력하는데 컬럼명을 이름과 연봉으로 출력하시오
    
    select ename as “이름”, sal*12 as “연봉”
    from emp
    where sal >= 3000;
  
  sal 대신 연봉을 쓰면 출력안된다 왜냐하면 실행순서 때문에 (실행순서 // from → where → select)
  
  문제17. 직업이 salesman 인 사원들의 이름과 직업을 출력하시오
    
    select ename, job
    from emp
    where job=’SALESMAN’;
  
  문제 18. 월급이 1000에서 3000 사이인 사원들의 이름과 월급을 출력하시오
    
    select ename, sal 
    from emp
    where sal <= 3000 and sal >=1000;
  
    selct ename, sal
    from emp
    where sal between 1000 and 3000;


## between and 연산자

  
  문제 19. 월급이 1000에서 3000사이가 아닌 사원들의 이름과 월급을 출력하시오
 	 
     select ename, sal
     from emp
     where sal not between 1000 and 3000; 

**년도 데이터 형식확인**

  년도 데이터를 검색할때에는 현재 내가 접속한 프로그램에 날짜 형식이 어떻게 되어있는지 확인을 하고 날짜 검색을 해야 제대로 검색할수 있다.
  확인하는 방법?
    
    select *
    from nls_session_parameters;
    NLS stands for national language support
  *동양 서양 날짜형식 주의 필요*
  
  문제 20. 81년 12월 11일에 입사한 사원의 이름과 입사일 출력
    
    select ename, sal
    from emp
    where hiredate='11/Dec/81';
    
  문제 21. 1981 년에 입사한 사원들이 이름과 입사일을 출력
    
    select ename, hiredate
    from emp
    where hiredate between '1/Jan/81' and '31/Dec/81'; 
  
  문제 22. 직업이 SALESMAN 이 아닌 사원들의 이름과 직업을 출력하시오.
    
    select ename, job
    from emp
    where job !='SALESMAN'; 
            
  문제23. 부서번호가 30번이 아닌 사원들의 이름과 부서번호 출력
   
    select ename, deptno
    from emp
    where deptno !=30;

## 기타비교연산자 4가지

  1. between and
  2. like
  3. in
  4. is null

## like 연산자

  ex) 이름의 첫번째 철자가 s로 시작하는 사원들의 이름을 출력하시오!
  	
    select ename
    from emp
    where ename like ‘S%’;
  	(% : wild card 이 자리에 뭐가 와도 관계 없다. wild card 로 인식되려면 꼭 like 로 써야함)


## 문자 -  single quotation mark
숫자는 필요 없음


  문제24. 이름의 끝글자가 T로 끝나는 사원이름 출력
    
    select ename
    from emp
    where ename like '%T';
  
  문제25. 이름의 두번째 철자가 M인 사원들의 이름을 출력하시오!
    
    select ename 
    from emp
    where ename like ‘_M%’;
  
  ! like 연산자를 사용할때 쓰는 키워드 
  '- _' : 이자리에 어떤게 와도 관계없는데 자릿수는 한자리
  
  문제 26. 이름의 세번째 철자가 L인 사원이름 출력
    
    select ename
    from emp
    where ename like '__L%';
  
  문제 27. 81년도에 입사한 사원들의 이름과 입사일을 출력하는데 between and 쓰지 말고
    
    select ename, hiredate
    from emp
    where hiredate like '%81';
  
  아래의 insert문을 실행해서 데이터를 입력하시오
  	
    insert into emp(empno, ename, sal)
  	values( 1234, ‘A%B’, 3500);
  	commit;
  
  문제 28. 이름의 두번째 철자가 %인 사원을 출력하시오
    
    select ename 
    from emp
    where ename like '_m%%' escape 'm';
                    
  문제 29. 이름의 두번째 철자와 세번째 철자 %인 사원의 이름 출력
    
    select ename 
    from emp
    where ename like '_m%m%%' escape 'm';
  
  문제 30. 이름의 첫번째 철자가 S로 시작하지 않는 사원 이름 출력
    
    select ename
    from emp
    where ename not like 'S%';

## in 연산자

  문제 31.  사원번호가 7788,7902, 7369 번인 사원들의 사원번호와 이름을 출력하시오
    
    select empno, ename
    from emp
    where empno in (7788,7902,7369);
  
  문제 32. 직업이 salesman, analyst 인 사원들의 이름과 직업을 출력하시오 ~
    
    select ename, job 
    from emp
    where job='SALESMAN' or job='ANALYST';
  
    select ename, job 
    from emp
    where job in('SALESMAN' ,'ANALYST');
  
문제 33. 직업이 SALESMAN, ANALYST 가 아닌 사원들의 이름과 직업을 출력
	
    select ename,job 
    from emp
    where job not in ('SALESMAN','ANALYST');
  
  문제 34. comm 이 null 인 사원들의 이름과 커미션 출력
 
    SELECT ename, comm 
    from emp
    where comm is null;    
  
  pb. 35. print out job, commission of employees whose job is SALESMAN and whose commission is not null and sort it in descending order, and make 
  문제 35. comm이 null 아니고 직업이 SALESMAN인 사원들의 이름과 월급과 직업과 커미션을 출력하는데 커미션이 높은 사원부터 출력하고 컬럼명을 이름, 월급, 직업, 커미션 한글로 출력되게 하시오
   
    SELECT ename as "이름", sal as "월급", comm as "커미션"
    from emp
    where comm is not null and job='SALESMAN'
    order by comm desc;  
  
  
  
  ## 

## Database connection to team leader using Gate**

    192.168.19.3
    유저이름: scott
    패스워드: tiger
    서비스이름: xe
    접속모드: default

    ALTER SESSION SET nls_date_format ='RRRR/MM/DD';
    INSERT INTO EMP2
            VALUES(5,'정호진',32,'1987/09/22','물리학','tbop02@gmail.com','010-2985-9834','서울시 광진구 화양동','LGT');
    COMMIT;

  문제 36. 이름과 전공과 나이를 출력하는데 나이가 높은 학생부터
    
    SELECT ename,major, age
    FROM EMP2
    ORDER BY age DESC;
  
  문제 37. 나이가 27에서 32사이인 학생들의 이름과 나이와 전공과 주소를 출력하시오
    
    SELECT ename, age, major, address
    FROM EMP2
    WHERE age BETWEEN 27 AND 32;  (where age >=27 and age <=32;)
  
  문제 38. 성이 김씨인 학생들의 이름과 나이를 출력하시오
    
    SELECT ename,age
    FROM EMP2
    WHERE ename LIKE '김%';
  
  problem 39. print name and major of students whose majo
  SELECT ename, major
  문제 39. 전공이 컴퓨터 관련 학과가 아닌 학생들의 이름과 전공
    
    select ename, major
    FROM EMP2
    WHERE major NOT LIKE '%컴퓨터%';

## 논리 연산자 (logic operator)**


  and, or, not
  
  True and Null → Null 
  (because we do not know whether Null is True or False)
  True or Null → True
  (no matter what Null is, answer should be True)
  False or Null → Null
  False and Null → False
  
  
  problem 40. print name, salay and job of employees whose job is SALESMAN and whose salary is more then 1200.
  문제 40. 직업이 SALESMAN 이고 월급이 1200이상인 사원들의 이름과 월급과 직업을 출력하시오.
  
    SELECT ename, sal, JOB
    FROM EMP
    where sal >= 1200 and job=’SALESMAN’;
  
  
  Problem 41.print name, salary and department number of employees whose commission is null and dept.
  문제 41. 커미션이 null 이고 부서번호가 20번인 사원들의 이름과 월급과 부서번호와 커미션을 출력하시오.
   
    SELECT ename, sal, deptno
    FROM EMP
    WHERE COMM IS null AND deptno=20;
  
  
  problem 42. print name, age and major of students whose major is related to computer and whose age is 20s. 
  문제 42. 전공이 컴퓨터 관련학과이고 나이가 20대인 학생들의 이름과 나이와 전공을 출력하시오.
  
    SELECT ename, age ,major
    FROM EMP2
    WHERE major LIKE '%컴퓨터%' 
    AND age between 20 and 29;
  
  (do not use age like ’2%’)
  
  문제 43. print out name, address and telecom company of students whose city is seoul and whose telecom company is SK.
  주소가 서울이면서 통신사가 sk인 학생들의 이름과 주소와 통신사를 출력하시오.
  Problem 43. print  name, address and telecom 
    
    SELECT ename,address, telecom
    FROM EMP2
    WHERE address LIKE '서울%' AND telecom like 'sk%;


**user creation**

 	create user scott
    identified by tiger;
  
 	grant dba to scott; 
  	(give dba permission to scott)
  
  	show user;
  	(confirm user name)
  
  	sqlplus scott/tiger (connect as scott)

**link** 

    create database link our_class_link
    connect to scott
    identified by tiger
    using ’192.168.19.3:1521/xe’;

    create table emp2
    as
    select * from emp2@our_class_link;
  
  Problem 44. print name, age and major of students whose major is not related to computer, and sort by age in descending order and change column name to 이름, 나이 and 전공.
      
      SELECT ename, age, major
          FROM EMP2
      WHERE major NOT LIKE '%컴퓨터%'
      ORDER BY age DESC;

## Priority of operator

  priority of logic operator
    ex)
    
    select ename, sal, job
    from emp
    where job=’SALESMAN’
    or job=’ANALYST’
    and sal > 1500;
    
   which logic operator will be executed first?
   answer) and

  problem 55. change the above query as ‘or’ can be executed first.
  → just use parentheses

