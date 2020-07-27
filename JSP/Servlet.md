### 서블릿(Servlet)
- 자바를 사용하여 웹을 만들기 위해 필요한 기술
- 클라이언트의 요청에 대해 동적으로 작동하는 웹 어플리케이션 컴포넌트
- HTML을 사용하여 요청에 응답한다.
- Java Thread를 이용한다.
- HTTP을 지원하는 javax.servlet.http.HttpServlet 클래스를 상속받는다.
- HTML 변경 시 Servlet을 재 컴파일해야 하는 단점이 있다.

## 매핑
  (1) web.xml
    <!-- 1. 서블릿으로 사용할 클래스-->
			<servlet>
			<servlet-name>MyServlet</servlet-name> <!-- 대상으로 한 클래스 이름 -->
			<servlet-class>org.joonzis.ex.Ex01_servlet</servlet-class>	<!-- 대상으로 할 클래스 패스 -->
		  </servlet>
      
		<!-- 2. 서블릿과 URL 간의 매핑 -->
		 	<servlet-mapping>
		 	<servlet-name>MyServlet</servlet-name>
			<url-pattern>/welcome</url-pattern>	<!-- 웹 주소에서 MyServlet을 welcome으로 부르자! ★무조건 슬래시(/)로 시작한다! -->
		 	</servlet-mapping>
      (2) 어노테이션
			- 서블릿 3.0 버전부터는 @WebServlet 어노테이션을 사용하면 web.xml에 등록하지 않아도 된다.
			- 톰캣 7~ 서블릿 3.0 지원
