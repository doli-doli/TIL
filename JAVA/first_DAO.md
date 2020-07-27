# 첫 DAO 파일
- 처음으로 만들어본 DAO클래스 파일

## 기본 DAO 형식
~~~
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

public class testDao {

	private Connection conn = null;
	private PreparedStatement ps = null;
	private ResultSet rs = null;
	private String sql = null;
	
	private testDao() {}
	private static testDao dao = new testDao();
	public static testDao getInstance() {
		return dao;
	}
	
	private Connection getConnection() {
		try {
			Class.forName("oracle.jdbc.driver.OracleDriver");
			String url = "jdbc:oracle:thin:@localhost:1521:xe";
			String user = "root";
			String password = "admin";
			conn = DriverManager.getConnection(url, user, password);
		} catch (Exception e) {
			e.printStackTrace();
		}
		return conn;
	}
	
}
~~~

## ArrayList 사용 (DAO)
~~~
public List<testDto> getAllList() {
	
	List<testDto> list = new ArrayList<testDto>();

	try {
		conn = getConnection();
		sql = "select * from green order by idx";
		ps = conn.prepareStatement(sql);
		rs = ps.executeQuery();

	while (rs.next()) {
		testDto dto = new testDto();
		dto.setIdx(rs.getInt("idx"));
		dto.setId(rs.getString("id"));
		dto.setPw(rs.getString("pw"));
		dto.setName(rs.getString("name"));
		dto.setAge(rs.getInt("age"));
		dto.setAddr(rs.getString("addr"));
		dto.setReg_date(rs.getDate("reg_date"));
		list.add(dto);
		}
	} catch (Exception e) {
		e.printStackTrace();
	} finally {
		try {
			if (rs != null) { rs.close(); }
			if (ps != null) { ps.close(); }
			if (conn != null) { conn.close(); }
		} catch (Exception e2) {
			e2.printStackTrace();
		}
	}
return list;
}
~~~
## JSP파일
~~~
<%
List<GreenDto> list = testDao.getInstance().getAllList();
%>
<table>
	<%if(list.size() > 0){%>
		<%for(GreenDto dto : list){ %>
		<tr>
			<td><%=dto.getIdx() %></td>
			<td><%=dto.getId() %></td>
			<td><%=dto.getPw() %></td>
			<td><%=dto.getName() %></td>
			<td><%=dto.getAge() %></td>
			<td><%=dto.getAddr() %></td>
			<td><%=dto.getReg_date() %></td>
		</tr>
		<%} }else {%>
	<%}%>
</talbe>
~~~
