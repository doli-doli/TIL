# SQL
  - 사용해본 쿼리문 추가
  
  ## 순서
  1. Connection conn = DBConnect.getConnection();
  2. String sql = 쿼리문 delete from sample where id=? and pw=?;
  3. PreparedStatement ps = conn.prepareStatement(sql);
  4. ps.setString(1, id); ps.setString(2, pw);
  5. int result = ps.executeUpdate();
  
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
  insert into member values(sample_seq.nextval, ?, ?);
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
  
