# JavaScript

    
## 스크립틀릿 안에서 alert쓰기    
~~~
<%
    if(result > 0 ){
			out.println("<script>");
			out.println("alert('회원 삭제 성공!')");
			out.println("location.href = 'view_all.jsp'");
			out.println("</script>");
		}
		else{
			out.println("<script>");
			out.println("alert('회원 삭제 실패!')");
			out.println("history.go(-1)");
			out.println("</script>");
		}
%>
~~~
