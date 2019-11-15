---
title: 2019年11月13日 日报 
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## Servlet
	生命周期
	指的是Servlet从创建到消亡的周期.
	servlet的创建时机:默认情况,当用户第一次访问servlet的映射地址时,对象创建.
	servlet的销毁时机,当tomcat关闭,或项目从tomcat删除时,servlet被销毁

	三个方法的体现:
	1.init方法:此方法在对象创建后执行.
	2.servlet方法:服务方法,当用户每一次访问时,执行,用于处理用户的请求,以及对用户进行响应.
	3.destroy方法:当tomcat关闭或项目从tomcat删除时,执行;

	ServletConfig
	是Servlet的配置对象,每一个Servlet都拥有一个ServletConfig
	我们在Web.xml进行Servlet配置时,可以向一个Servlet中添加初始化的参数,
	这些参数以键值对的形式存储在ServletConfig中
	在web.xml中,想ServletConfig存储数据格式:
	<Servlet>
	..	
	<!--init-param标签可以存在多个,每一个init-param都表示一个键值对-->
	param是参数的意思是
	<init-param>
	<param-name>键</param-name>
	<param-value>值</param-value>
	</init-param>
	</Servlet>
	在Servlet中得到ServletConfig对象的方式:
	方式1与方式2是互斥的
	方式1:
	在Servlet中重写Servlet周期init(ServletConfig config)方法,使用方法参数中的config对象
	方式2:
	在Servlet的任意代码位置,通过getServletConfig方法得到对象
	从ServletConfig中取出数据的格式:
	config对象.getInitParamter(String 键值对的键);

	接受用户表单的参数
	1.根据一个name,接收单个参数
	String value=request.getParameter(String name);

	2.根据一个name,接收一组参数
	String[] value=request.getparameterValues(String name);

	HttpGET请求和HttpPOST请求的区别:
	GET请求:
	在网址中,编写在?后,由1个或多个键值对组成,键与值之间使用等号连接,多个键值之间使用&分隔.
	只能传字符串类型的参数
	网址的最大长度为4kb 通常支持的文字大小2048个
	数据传输不安全
	tomcat8+版本:GET请求不会乱码
	POST请求:
	请求的数据,以键值对的形式存储在请求体中,
	请求体是一个单独的数据包,较GET请求而言,安全.
	可以传输任意类型的数据
	数据的大小,理论上是无上限的(看服务器或本地的硬件能力)
	tomcat8+版本:POST请求默认编码为 ISO-8859-1(不支持中文)
	什么样的请求是GET请求
	以我们目前所学习的技术来说,除了表单提交时method="post",其他的访问方式都是GET请求
	例如:
	点击超链接访,问网址
	通过js:Window.location.href=' '访问
	浏览器中输入网址 + 回车
	表单提交时,method="GET"或默认
	ajax的GET请求
	java代码的URL类的GET请求
	什么样的请求是POST请求
	例如:
	表单提交时method="POST"
	ajax的POST请求
	java代码的URL类的POST请求

	解决GET和POST的乱码问题:
	请求的乱码问题:
	客户机到服务器
	正常文字-->UTF-8编码-->字节数组-->ISO-8859-1编码-->乱码文字
	服务器到客户机
	正常文字<--UTF-8编码<--字节数组<--ISO-8859-1编码<--乱码文字
	1.将乱码的文字,通过ISO-8859-1编码打碎成字节数组
	byte[] bytes=变量名.getByte("ISO-8859-1");
	2.通过UTF-8编码将字节数组重新组装为正常文字
	变量名=new String(byte,"utf-8");
	解决乱码的两种格式:
	格式1:可用于解决tomcat8版本之前的GET请求乱码以及所有版本的POST请求乱码
	解决方案:将乱码的文字按照乱码的编码ISO-8859-1转换为字节数组,再按照正常的编码UTF-8组装为正常文字;
	格式2: 
	格式1解决乱码适用于参数较少的情况下,如果参数过多解决起来极其麻烦
	tomcat为我们提供了设置请求体编码的方式:
	注意:只有POST请求才有请求体,
	格式:request.setCharacterEncoding("UTF-8");
	注意:
	解决乱码的代码,必须运行在获取参数之前
	request.setCharacterEncoding("UTF-8")必须执行在获取参数之前;
	响应的乱码问题:
	方式1:
	设置网页的内容类型,以及网页的编码格式
	response.setContentType("text/html;charset=utf-8");
	方式2:
	设置网页的编码格式(因为没有设置网页类型为HTML,所以浏览器解析时也是乱码)
	response.setCharacterEncoding("UTF-8")
	注意:
	设置响应乱码的两种方式都必须写在响应内容之前,都必须写在响应内容之前













