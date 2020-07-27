# SQL
  - 사용해본 쿼리문 추가
  
  ## CREATE(JSP 파일)
  - create table
  ~~~
  create table sample ( "
	+ " no number primary key, "
	+ " name varchar2(20) not null, "
	+ " reg_date date not null)";
~~~
  - create sequence (1씩 증가하는 시퀀스)
 ~~~
 create sequence sample_seq start with 1 increment by 1
 ~~~
 - insert
  ~~~
  insert into member values(member_seq.nextval, ?, ?, ?, ?, ?, sysdate);
  ~~~
  - update
  ~~~
  update sample set name = ? where name = 'bart'
  ~~~
  - delete
  ~~~
  delete from sample where id=? and pw=?;
  ~~~
  - select
  ~~~
  select * from sample order by ?;
  ~~~
