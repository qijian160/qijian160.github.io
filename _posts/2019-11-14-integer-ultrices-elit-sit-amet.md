---
title: 2019年11月14日 日报 
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## jsp
	sinclude指令
	用于将一个JSP或html文件引用到另一个JSP当中
	格式:
	<%@ include file="引入的路径"%>

	include动作
	用于将一个JSP或HTML文件引入到另一个JSP中
	格式:
	<jsp:include page="引入的路径" flush="true"/>
	include指令和include动作的区别:
	include执行相当在用户访问前先把代码复制过来再用jsp引擎转换为servlet
	include动作相当于在用户运行的时候临时把文件引用过来
	JSP的内置对象(隐含对象):
	内置对象指的是:JSP引擎在转换JSP文件时,帮我们的代码在执行之前,创建一些供我们使用的对象,
	内置对象具备大量的JSP中的常用功能,使用JSP内置对象可以大大的简化我们的开发流程.
	JSP的九大内置对象:用<%圈起来%>
	最常用的5个{
	request:
	类型:HttpServletRequest
	作用:请求对象,包含了请求相关的信息和参数
	response:
	类型:HttpServletResponse
	作用:响应对象,包含一些用于响应的功能
	out:
	类型:JSPWriter
	作用:是打印流,用于向响应体中,输出数据
	Session:
	类型:HttpSession
	作用:会话对象,用于状态管理以及会话跟踪.
	application
	类型:ServletContext
	作用:Servlet的上下文,一个应用内存中同时只有一个上下文对象,用于多个Servlet或JSP之间进行通信,
	}
	config:
	类型:ServletConfig
	作用:Servlet的配置对象,用于配置一些初始的键值对信息
	PageContext:
	类型:PageContext
	作用:页面的上下文,每一个JSP都拥有一个JSP对象,用于多段代码之间进行通信
	exception:
	类型:Throwable
	作用:当页面的page指令中isErrorPage属性值为true时,才会存在此对象,用于收集错误信息,通常此对象为null,只有其他页面指定errorPage=当前页面时,且发生BUG后,跳转到此页面时,对象才不为null
	page(最没有用的对象):
	类型:Object
	作用:指当前JSP页面本身,在JSP引擎生成的代码中,page对象的赋值为:
	Object page=this;
	JSP四大域对象
	九大隐含对象中,包含了四个较为特殊的隐含对象,这四个对象我们称其为域对象,他们都具备存储数据/删除数据/获取属性值的方法:
	存储数据:setAttribute(String key,Object value);
	获取数据:object value=getAttribute(String key,);
	删除数据:remoAttribute(String key);
	这四个域对象,'域'指的是作用域,分别是:
	pageContext:页面的上下文	作用域:一个JSP页面
	request:请求对象			作用域:一次请求(一次请求可以经过转发,一次请求可能包含多个JSP页面)
	session:会话对象			作用域:一次会话(一次会话可能包含多次请求)
	application:servlet上下文对象	作用域:一次服务(服务器的启动到关闭)(一次服务可能包含多个会话)

	JSP动作
	jsp useBean动作(熟悉熟悉)
	作用:向四大域中,存储bean对象.
	格式:
	<jsp:useBean  id="存储时的key"    scope="page或request或session或application"存储的范围    class="要存储的对象类型"> </jsp:useBean>
	jsp useBean+ setProperty动作
	作用:向四大域对象中存储bean对象并设置属性值
	格式:
	<jsp:useBean>
	id="存储时的key "
	scope="page或request或session或application"存储的范围
	class="要存储的对象类型"
	</jsp:useBean>
	<jsp:setproperty name="存储时的key" property="属性名" value="属性值"/>
	//serproperty可以出现多次
	jsp useBean+ setProperty动作 快速获取表单提交的内容
	格式:
	<jsp:useBean>
	id="存储时的key "
	scope="page或request或session或application"存储的范围
	class="要存储的对象类型"
	</jsp:useBean>
	<jsp:setproperty name="存储时的key" property="属性名" value="属性值"/>
	注意:如果seproperty动作中property的值既是对象的属性名又是我们用户请求的参数的名称的,自动将参数获取到,并赋值给对象
	JSP getproperty动作
	作用:从四大域对象  取出某个对象的属性,并显示到网页中
	语法格式:
	<jsp:getproperty name="对象存储时的key" property="属性名">





