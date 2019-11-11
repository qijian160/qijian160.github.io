---
title: 2019年11月8日 日报 
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## JDBC
  JDBC访问数据库的步骤(面试题)
	1.加载驱动
	Class.forName("包名.驱动名")
	2.获取连接 Connection
	DriverManager.getConnection(url,username,password);
	比如:连接Oracle的url是jdbc:oracle:thin:@127.0.0.1:1521:xe
	3.定义sql 并获取sql的执行环境Statement
	conn.createstatement()     这里以后会换成prepareadStatement
	4.执行sql处理sql返回值
	select   返回ResultSet(结果集)     遍历   st.executeQuery
	dml       返回int   代表影响的数据行数     st.executeUpdate
	5.释放资源
	Connection  Statement    ResultSet  
	OJDBC.JAR包就是一堆class文件的压缩包
	sql返回值处理的技巧
	在查询处理sql返回值的时候,如果只查一条用if(rs.next)即可,但是如果查多条就要用多条whlie(rs.next)

	3.使用preparedStatement替换Stetment
	1.可以防止拼接的sql注入攻击,原理就是输入的数据不拼接,直接作为真实数据
	2.由于采用预编译,会提前生成sql的执行计划,提高执行效率
	3.拼接sql 每次sql是不同的  这会给数据库服务器的sql缓冲造成冲击,无法实现批处理而它可以防止此类事件发生
	4.由于不拼接sql,程序员出错的概率会降低
	5.select * from BANK where USERNAME=?and PASSWORD=?可以用?代替要添加的数据,
	工具类思想:
	负责获取数据库的连接以及资源的释放,提高代码的复用度
	配置文件思想:
	思想就是:可以不修改源代码的情况下修改参数数据
	获取类加载器并获取资源:类名.class.getclassloader().getResourceAsStream("资源名");
	InputStream in=类名.class.getclassloader().getResourceAsStream("资源名");
	加载流中的资源
	Properties pro=new Propeties();
	//加载流中的key value()
	pro.load(inputStream);
	//可以从pro中取出key对应的值,
	就直接用driverClassName=pro.getproperty("资源文件中定义的键名");
	executeQuery和executeUpdate的区别
	executeQuery是用来查看select等的返回信息,
	executeUpdate是用来查看增删改的影响行数

	DAO接口(重点,天天用)
	什么事DAO?
	Data Access Object  数据访问对象  
	它是对数据访问过程封装的对象
	如何编写DAO?
	1.根据需求编写DAO对应的接口
	2.使用DBUtil工具类结合JDBC编程的五步 实现接口中对应的方法
	接口定义的3部分
	1.接口定义的返回值类型
	2.方法的名字
	3.方法的参数