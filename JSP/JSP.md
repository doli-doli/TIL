# JSP

## JSP(Java Server Page)
  - HTML 파일 내에 Java언어를 삽입한 문서
  - 동적 웹 어플리케이션 컴포넌트
  - .jsp 확장자
  - 요청에 동적으로 작동하고, 응답은 html을 이용
  - jsp는 servlet으로 변환되어 실행 되고 .jsp.java로 변환, .jsp.class로 컴파일된다.
  
## JDBC
  - 자바에서 데이터베이스에 접속할 수 있도록 하는 자바 API이다. 
  - JDBC는 데이터베이스에서 쿼리 또는 업데이트하는 방법을 제공한다.
  
  ## 데이터베이스 연결 순서
1. JDBC드라이버 로드 - DriverManager
    - `Class.forName("oracle.jdbc.driver.OracleDriver");` 메모리에 OracleDriver가 로드된다.
2. 계정정보 연결 (url , ID , PASSWORD )
    - `String url = "jdbc:oracle:thin:@localhost:1521:XE";` 접속 URL정보 포트(oracle포트), sid(oracle버전)
    - `String user = "DB아이디";
    - `String password = "DB비밀번호";
3. 데이터베이스 연결 - Connection
    - `DriverManager.getConnection(url, user, password);` Connection 객체 생성
4. SQL문 실행 - Statement
    - `connection.createStatment();` Statement 객체를 통해 SQL문이 실행된다.
5. close();

- JDBC 연결
  ~~~
  String driverName = "oracle.jdbc.driver.OracleDriver";
	String url = "jdbc:oracle:thin:@localhost:1521:XE";
  String user = "DB아이디";
  String password = "DB비밀번호";
	Class.forName(driverName);
	Connection con = DriverManager.getConnection(url, "user", "password"); 
  ~~~
