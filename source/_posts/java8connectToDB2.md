---
title: Java 8 connect to DB2
date: 2018-02-26 09:48:40
categories:
	- Develop
tags:
	- Java
	- DB2
	- IntelliJ IDEA
---

讓 Java 8 可以連線到 DB2

<!-- more -->

## Java 8 connect to DB2

### Install DB2

\> [`IBM Data Server Runtime Client.msi`]() <

-- 若已經裝了`WebSphere Application Server(WAS)`應該就有裝過了

### Enable DB2Driver

-- 已經加入在目錄下 --

>複製 `db2jcc.jar` & `db2jcc_license_cu.jar` 到 `main/webapp/WEB-INF/lib/`目錄下
>![](jdbc-lib.png)

>加入兩個jar檔至專案：
>
>File > Project Structure > Modules > <xxxx>_main > Dependencies > +
>
>加入WEB-INF/lib 下的 db2 jar檔


![](intellij-project-structure-1.png)

![](intellij-project-structure-2.png)

### Enable JdbcOdbcDriver

> 解壓縮 > [`rt.jar`]() <
>
> 將`sun`目錄下的`jdbc` & `security/action`兩個資料夾複製到 新的`sun`目錄下
>
> ps.目錄結構不要改變
>
> 使用`cmd` 開啟路徑至 新的`sun`目錄
>
> Enter `jar -cvf jdbc.jar sun` 將`sun`目錄打包成 `jdbc.jar`

![](jdbc-lib-2.png)

> 將> [`jdbc.jar`]() <複製到 `C:\Program Files\Java\jdkx.x.x_xxx\jre\lib\ext`目錄下

> 將> [`jdbcOdbc.dll`]() <複製到 `C:\Program Files\Java\jdkx.x.x_xxx\jre\bin` 目錄下


## 使用

``` java
public Connection getDB2Connection() throws SQLException,ClassNotFoundException{
	String user = "<user>";
	String password = "<password>";
	String JDriverAS = "sun.jdbc.odbc.JdbcOdbcDriver";
	String SQlServerDriver = "com.ibm.db2.jcc.DB2Driver";
	String dbConnectionStr = "jdbc:db2://<ip:port>/<db>";
	try {
		Class.forName(JDriverAS);
		Class.forName(SQlServerDriver);
		connection = DriverManager.getConnection(dbConnectionStr, user, password);
	} catch (SQLException ex) {
		System.err.println("Connection Fail !!");
		System.err.println(ex.toString());
	}
	return connection;
}
```

``` java
try{
	Connection conn_db2 = getDB2Connection();
	String sql = "select * from user";
	Statement stmt_db2 = conn_db2.createStatement();
	ResultSet rs = stmt_db2.executeQuery(sql);
	ArrayList<Map<String,Object>> dataList = DataSetUtil.setDataList(rs);
	stmt_db2.close();
}catch(Exception e){
	e.printStackTrace();
}finally{
	if(conn_db2!=null)
		conn_db2.Close();
}
```