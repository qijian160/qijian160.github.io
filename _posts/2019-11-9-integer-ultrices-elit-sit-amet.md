---
title: 2019年11月9日 日报 
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## JDBC
   事务:
	在dos命令操作oracle时,执行DML,需要结束事务(commit提交或rollback回退)
	在JDBC中,事务是自动提交的,每执行一条DML语句,事务就自动提交一次
	我们可以通过JDBC的事务API,开始事务的手动提交,将多条DML语句看作一个整体,要么一起成功,要么一起失败

	JDBC事务操作格式:  查看事务案例
	注意:开启事务的手动提交是通过连接对象按成的,某个数据连接对象的事务开启手动提交后,这个连接对象的事务需要手动控制,而其他连接对象不受影响
	操作方法:
	笔记中的conn都代表connection
	1.开启事务的手动提交:手动后sql语句执行完毕后数据库不会变化而是等待提交后再变化
	conn.setAutoCommit(boolean flag);
	参数含义:true表示自动提交,false表示手动提交
	2.提交事务:将提交放入最终的执行完毕处,以防程序执行中发生异常况导致数据库错误
	conn.commit();
	3.回退事务:将回退放入执行可能发生错误的地方,判断执行失败.如果执行失败就回退
	conn.rollback();
	批处理(了解)
	将多条sql语句放在一起批量处理,
	批处理将多次数据库的操作次数,减少到来了一次! 提高了大量sql语句一起还行时候的性能.
	使用步骤:
	批处理使用Statement类操作
	步骤1.将一条sql语句加入到批处理中
	statment.addBatch(String sql);  将是所有代码添加到批处理中
	步骤2.执行批处理中的所有语句
	statment.executeBatch();   执行批处理中的所有代码

	properties文件与类(键值对文件)
	properties文件常用语java中的配置文件
	因为properties文件可以快速的与properties类(在Map集合中)快速转换
	文件:
	注释:#开头就是注释行
	键值对:键与值之间使用等号连接,多个键值对之间使用换行分割
	如何将properties文件转换为Map集合对象:
	步骤:
	1.创建properties对象
	properties ppt=new properties
	2.得到properties文件的输入流,
	InputStream is= //可以通过new FileInputStream,也可以通过ClassLoader等等
	3.将流加载到properties对象中
	ppt.load(is)
	连接池
	由连接池创建连接,维护连接
	我们需要使用连接时,从连接池中获取连接.
	如果连接池中存在空闲连接,则拿去使用,
	如果不存在空闲连接,且池未满,则在连接池中创建新的连接使用.
	如果不存在空闲连接,且池已满,则排队等待空闲连接
	使用步骤
	1.引入相关的jar文件
	dbcp:连接池的代码库
	poll:连接池的依赖库
	2.创建一个properties文件,用来描述连接池的配置
	#数据库链接地址
	url=jdbc:oracle:thin@localhost:1521:XE
	#数据库的驱动地址
	driverClassName=oracle.jdbc.OracleDriver
	#数据库的账号
	username=system
	#数据库的密码
	password=123456
	#扩展配置
	#初始化连接池时,创建的连接数量:
	initialSize=5
	#最大允许存在的连接数量
	maxActive=200
	#空闲时允许保留的最大连接数量
	maxIdle=10
	#空闲时允许保留的最小连接数量
	minIdle=5
	#排队等待的超时时间(毫秒数)
	maxWait=20000
	3.将properties文件,转换properties对象
	properties ppt=new properties();
	ppt.load(文件输入流);
	4.通过连接池工厂类(BasiDataSourceFactory),创建连接池对象(一次程序启动,创建一个连接池就够了.)
	DataSource ds=BasiDataSourceFactory.createDatasource(ppt);
	5.通过连接池对象,获取连接池中的连接
	connection conn=ds.getConnection();
	6.正常JDBC操作