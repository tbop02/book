# 서브쿼리 튜닝

1. 옵티마이져란?
2. 쿼리변환
3. 서브쿼리 unnesting
4. 뷰 merging
5. 스칼라 서브쿼리를 이용한 조인
6. 수정가능 조인뷰
7. 분석함수를 이용한 SQL 튜닝





## 옵티마이져

SQL을 가장 효율적이고 빠르게 수행할 수 있는 최적의 처리경로를 선택해주는 DBMS의 핵심엔진이다

* SQL ----> 옵미타이져 ----> 실행계획
* 옵티마이져에 **테이블 분석정보**를 주어야 된다





## 쿼리변환

옵티마이져가 실행계획을 생성하기 전에 사용자가 작성한 SQL보다 결과는 똑같은데 비용이 더 적게 발생하는 SQL이 있다면 그 SQL로 알아서 쿼리를 변경을 한다.



EX) 이름이 EN 또는 IN을 포함하고 있는 사원들의 이름과 월급과 직업을 출력하시오

	SELECT /*+ leading(e3 e1) use_nal(e1)*/ e1.ename, e1.address, e1.age
	FROM EMP2 e1,
	(
	SELECT  /*+ index_ffs(e emp2_address) */ROWID rr
	FROM EMP2 e
	WHERE address LIKE '%송파%' or address LIKE '%동작%'
	) e3
	WHERE e1.rowid=e3.rr;

![1524554332479](C:\Users\tbop02\AppData\Local\Temp\1524554332479.png)


**hint에 no_merge 가 없어서 자동으로 변환했다**

	Select ename,sal,job
	from emp
	where ename like '%EN%' or
		ename like '%IN%';

### no_merge hint

* no merge hint 를 줌으로써 조인을 막을수 있다.




Pb 82.  (서브 쿼리의 쿼리 변환) DALLAS에 있는 부서번호에서 근무하는 사원들의 이름, 월급을 출력하는데 JOIN 사용하지말고 서브쿼리를 이용해서 작성 

    SELECT ename,sal
     FROM EMP
     WHERE deptno =
     (
     SELECT deptno 
     FROM DEPT
     WHERE loc='DALLAS');

![1524555593300](D:\Hojin\git\subquery_tunning_image\1524555593300.png)





Pb 83. 위의  SQL의 = 을 in 으로 바꿔서 수행해보시오

	 SELECT ename,sal
	 FROM EMP
	 WHERE deptno in
	 (
	 SELECT deptno 
	 FROM DEPT
	 WHERE loc='DALLAS');

![1524555244334](D:\Hojin\git\tuning_image\media\1524555244334.png)

**SEMI Join 을 실행했다 (절반의 조인을 실행)**



Pb 84. 세미조인하지 말고 서브쿼리로 수행하라고 힌트를 주시오

	SELECT ename,sal
	FROM EMP
	WHERE deptno in
	(
	SELECT /*+ no_unnest*/ deptno 
	FROM DEPT
	WHERE loc='DALLAS');

**/*+ no_unnest*/  강하게 감싸서 서브쿼리로 실행하라는 의미**

![1524555800930](D:\Hojin\git\subquery_tunning_image\1524555800930.png)

*위의 결과에서 optimizer가 자동으로 semi join을 하지 않을것을 알 수 있다.*



Pb 85. 아래의 SQL의 실행계획을 dept가 먼저 드라이빙 되면서 해쉬 세미조인 되게 하시오

	 SELECT /*+ leading(d e) use_hash(e) swap_join_inputs(d) */ e.ename,e.sal
	 FROM EMP e
	 WHERE deptno IN (SELECT deptno 
	 FROM DEPT d where loc='DALLAS');


![1524556621091](D:\Hojin\git\subquery_tunning_image\1524556621091.png)

 



### semi join 이란

* 일반적인 조인과는 다르게 첫번째 table 에 row가 한번만 return 된다. conventional join의 경우 rows 가 여러번 접근되는것에 차이점이 있다.
* where 절 서브쿼리로 in 이나 exist 로 접근할경우 자동으로 hasi semi 조인이 된다. 

