# JavaScript

## alert 쓰기
~~~
<script type="text/javascript">
alert("테스트 성공!");
history.back();
</script>
~~~

## 스크립틀릿 안에서 alert쓰기    
~~~
<%
    if(result > 0 ){
			out.println("<script>");
			out.println("alert('테스트 성공!')");
			out.println("location.href = 'test.jsp'");
			out.println("</script>");
		}
		else{
			out.println("<script>");
			out.println("alert('테스트 실패!')");
			out.println("history.go(-1)");
			out.println("</script>");
		}
%>
~~~
