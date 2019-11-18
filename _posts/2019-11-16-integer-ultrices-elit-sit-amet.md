---
title: 2019年11月16日 日报 
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## jsp
	JSP简介:
		Java Service Pages 是Java的动态网页技术.

		JSP引擎:
		引擎原理:
		JSP引擎用于将JSP文件转换为Servlet
		1.在服务器启动时,JSP引擎读取.jsp文件
		2.将文件转换为Servlet代码,并给Servlet添加映射地址为JSP的文件名称
		3.当用户浏览器访问jsp文件名称时,其实请求的不是jsp文件而是生成的Servlet
		4.Servlet负责给浏览器进行响应
		
		JSP语法结构:
		JSP保存的路径:web目录下
		JSP可以包含HTML代码,Java代码,以及JSP特有的标记
		Java代码的声明区:(很少用到)
		指的是Java的成员代码位置,在JSP声明区中编写的java代码,会生成到servlet的成员位置
		语法:
		<%!
		这里编写java代码,且会生成到声明区
		%>
		Java代码执行区:
		指的是Servlet的service方法中.用户每次请求都会执行
		语法:
		<%
		Java代码
		%>
		表达式
		用于快速的将java代码中的变量输出到网页中.
		语法:
		<%=变量名%>
		转换的java代码:
		out.print(变量名):
		JSP中编写注释:
		因为JSP文件包含了三种语法结构(java,html,jsp)
		所以,三种语法结构的注释,都可以起到注释的效果
		Html注释:
		<!--  -->
		在JSP中,HTML的注释会被JSP引擎认为是HTML代码,会转换为out.write("<!-- -->");
		跟在html中写注释是一样的
		java注释
		单行://
		多行/* */
		文档注释/**   */
		在JSP中java的注释会被JSP引擎认为是java代码,会原封不动的放到_jsp.java文件中.
		JSP注释:
		<%-- JSP注释 --%>
		在JSP引擎将JSP文件转换为.java文件时会忽略JSP注释的部分.

		JSP指令 
		指令格式:
		<%@ 指令名称 属性名=值,属性2=值.....属性n=值%>
		page指令
		用于设置页面:
		完整格式:
		<%page
		language="java"
		extends="继承的类"
		contentType="text/html;charset=utf-8";--内容类型以及编码格式
		(重点)errorPage="网页地址"--当JSP代码出错后页面由指定地址进行显示
		(重点)isErrorPage="true或false"--true表示当前页面是处理错误的页面.只有为true时,才可以查看异常信息.(使用这个后就可以在页面中使用java代码<%exception.printStackTrace();%>对错误信息进行打印)
		(重点)import="包1,包2,包3...." --属性值是一个或多个导入的包,包与包之间使用逗号隔开即可,
		一俩年内之内是碰不到以下四个{
		buffer="数值或none"--缓冲区,none表示不缓冲,默认是8kb大小
		session="true或false"--true表示自动创建session,false表示不自动创建
		autoFlush="true或false"--true表示缓冲器自动清除,默认为true
		isTherdSafe="true或false"--<%%>中的代码是否是同步.true表示是同步,默认false}
		%>

