# SQL
  - 사용해본 쿼리문 추가
  
  ## 순서
  1. Connection conn = DBConnect.getConnection(); DB 연결하고
  2. String sql = 쿼리문 delete from sample where id=? and pw=?; 쿼리작성하고
  3. PreparedStatement ps = conn.prepareStatement(sql); 쿼리담아서
  4. ps.setString(1, id); ps.setString(2, pw); 쿼리 빈칸 채우고
  5. int result = ps.executeUpdate(); 쏴주기!
  
  ## 사용
  - create table
  1. 클래스에서 사용
  ~~~
  create table sample ( "
	+ " no number primary key, "
	+ " name varchar2(20) not null, "
	+ " reg_date date not null)";
~~~
2. sql문
~~~
create table sample (
	no number primary key,
	name varchar2(20) not null,
	reg_date date not null);
~~~
  - create sequence (1씩 증가하는 시퀀스)
 ~~~
 create sequence sample_seq start with 1 increment by 1
 ~~~
 ## insert
  ~~~
  insert into member values(sample_seq.nextval, ?, ?);
  ~~~
  ## update
  ~~~
  update sample set name = ? where name = 'bart'
  ~~~
  ## delete
  ~~~
  delete from sample where id=? and pw=?;
  ~~~
  ## select
  - 기본 검색
  ~~~
  select * from sample order by ?;
  ~~~
  - between A and B
  
  employees(사원 테이블) 테이블에서 사원 아이디(employee_id)가 150~170 사이인 사원들의 email 현황을 조회합니다.
  
  ~~~
  select email from employees where employee_id between 150 and 170;
  ~~~
  - 별칭 사용하기 / AS 별칭
  
  employees(사원 테이블) 테이블에서 사원 아이디(employee_id)가 150~170 사이인 사원들의 email 현황을 "이메일" 이라는 별칭으로 조회합니다.
  ~~~
  select email as 이메일 from employees where employee_id between 150 and 170;
  ~~~
  
