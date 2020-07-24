# SQL
  - 사용해본 쿼리문 추가
  
  ## CREATE(JAVA 파일)
  - 전역변수 선언 
  ~~~
  Connection conn = null;
  PreparedStatement ps = null;
  ~~~
  - create table
  ~~~
  String sql = "create table sample ( " 
			 + " no number primary key, "
			 + " name varchar2(20) not null, "
			 + " reg_date date not null)";
  execute();
  ~~~
  - create sequence (1씩 증가하는 시퀀스)
  `String sql = "create sequence sample_seq start with 1 increment by 1";`
  - insert
  ~~~
  String sql= "insert into sample (no, name, reg_date) " + "values (sample_seq.nextval, ?, sysdate)";
  executeUpdate();
  ~~~
  - update
  ~~~
  String sql= "update sample set name = ? where name = 'bart'";
  executeUpdate();
  ~~~
  - delete
  ~~~
  String sql= "delete from sample where no = ?";
  executeUpdate();
  ~~~
  - select
  ~~~
  String sql= "select * from sample";
  executeQuery();
  ~~~
