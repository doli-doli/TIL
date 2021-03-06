# JSP

## JSP(Java Server Page)
- HTML 파일 내에 Java언어를 삽입한 문서
- 동적 웹 어플리케이션 컴포넌트
- .jsp 확장자
- 요청에 동적으로 작동하고, 응답은 html을 이용
- jsp는 servlet으로 변환되어 실행 되고 .jsp.java로 변환, .jsp.class로 컴파일된다.
  
## JSP 태그종류
- <% 스크립틀릿, java code %>
- <%= 표현식, 결과값 출력 %>
- <%@ 지시자, 페이지 속성 %>
- <%-- 주석 --%>
- <%! 선언, 변수 메서드 선언 %>
- jsp:action 자바 빈 연결 </jsp:action>

## 태그 사용
1. <%@ page %>
- import문에 많이 사용
~~~
<%@page import="com.jh.ex.*"%>
<%@ page import="java.sql.*"%>
<%@taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
~~~

2. <%@ include %>
- file 속성 사용
`<%@ include file="index.jsp"%>`

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

- DB 연결
~~~
String driverName = "oracle.jdbc.driver.OracleDriver";
String url = "jdbc:oracle:thin:@localhost:1521:XE";
String user = "DB아이디";
String password = "DB비밀번호";
Class.forName(driverName);
Connection con = DriverManager.getConnection(url, "user", "password"); 
~~~

## PreparedStatement 객체
- SQL문 실행을 위해 사용하는 Statement 객체 스스로는 SQL 구문 이해 못함 -> 전달역할
- Statement 객체의 중복코드 단점을 보완한 객체
~~~
Connection conn = null;					
PreparedStatement ps = null;

try {
	conn = DBConnect.getConnection();
	String sql = "create table sample ( " 
			 + " no number primary key, "
			 + " name varchar2(20) not null, "
			 + " reg_date date not null)";
	ps = conn.prepareStatement(sql);
	ps.execute();
} catch (Exception e) {
	e.printStackTrace();
} finally {
	try {
		if( ps != null ) { ps.close(); }
		if( conn != null ) { conn.close(); }
	} catch (Exception e) {
		e.printStackTrace();
	}
}
~~~

## DBCP (Data Base Connection Pool)
- 다수의 요청이 발생할 경우 데이터베이스에 부하가 발생함
- 미리 커넥션 객체들을 만들어 놓는 커넥션 풀 기법 사용

### 주요속성
1. name : 현재 Resource를 등록 할 이름
2. type : 현재 Resource의 타입
3. maxTotal : 생성할 커넥션의 숫자 ( == maxActive :버전차이)
4. maxIdle :  Connection Pool에서 사용하지 않고 대기하는 최대 Connection의 개수(음수로 설정하면 제한 없음)
5. maxWaitMillis : 최대 대기 시간 , (음수로 설정하면 제한 없음)( == maxWait)

## DBCP 사용해보기
- context.xml파일 WebContent->Meta-INF저장
~~~
<Context>
	<Resource
		name="jdbc/oracle"
		driverClassName="oracle.jdbc.driver.OracleDriver"
		url ="jdbc:oracle:thin:@localhost:1521:xe"
		username="root"
		password="admin"
		maxTotal="8"
		maxIdle="2"
		maxWaitMillis="5000"
		type="javax.sql.DataSource"
		/>
</Context>
~~~

## EL(Expression Language)
- JSP 에서 사용하는 새로운 스크립트 언어
- 표현식을 대체하는 역할 
	1. <%= 변수값 %>
	2. <%= 계산식 %>
	3. <%= 함수() %>
- 4가지 영역(객체)에서 사용

### pageContext
1. 하나의 페이지를 처리할 때 사용하는 영역
2. page 영역
3. 해당 페이지를 벗어나면 데이터가 삭제됨
### request
1. 하나의 요청을 처리할 때 사용하는 영역
2. request 영역
3. response 하면 데이터가 삭제됨
### session
1. 하나의 웹 브라우저를 처리할 때 사용하는 영역
2. session 영역
3. 웹 브라우저를 종료하면 데이터가 삭제됨
### application
1. 하나의 웹 에플리케이션에서 사용하는 영역
2. application영역
3. 웹 어플리케이션을 종료하면 데이터가 삭제됨

## EL 내장객체
- ${param } : 요청 파라미터를 참조하는 객체
- ${paramValues } : 요청 파라미터(배열)를 참조하는 객체
- ${pageScope } : 페이지 객체를 참조하는 객체
- ${requestScope } : request 객체를 참조하는 객체
- ${sessionScope } : session 객체를 참조하는 객체
- ${applicationScope } : application 객체를 참조하는 객체
- ${initParam } : 초기화 파라미터를 참조하는 객체
- ${cookie } : cookie 객체를 참조하는 객체

## 파일 U&D
- 파일 업로드 다운로드
	1. cos.jar 파일 빌드패스
	2. WebContent -> 폴더생성 -> 해당위치를 업로드 위치로 사용
	3. 폼 태그`<form method="post" enctype="multipart/form-data">`
	4. 일반 request 대신 MultipartUrequest 클래스를 사용한다.
