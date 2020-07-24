# TIL

<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>1 ~ 100 사이 짝수 합 구하기</title>
</head>
<body>
	<%
		int evenTotal = 0;
		for (int n = 1; n <= 100; n++){
			if( n % 2 == 0) {
				evenTotal += n;
			}
		}
		// 다른 페이지로 결과를 전달하기 위해 request 영역(객체)에 저장하기
	 	request.setAttribute("EVEN", new Integer(evenTotal));
		
		// 02_attribute2.jsp 파일로 request를 보내기!
		// 시스템의 변화가 없는 상태에서 이동하는 경우 "포워드"를 이용한다!
		 request.getRequestDispatcher("02_attribute2.jsp").forward(request, response);
		// == RequestDispatcher dispatcher = request.getRequestDispatcher("02_attribute2.jsp");
		// 	  dispatcher.forward(request, response);
	%>
</body>
</html>
