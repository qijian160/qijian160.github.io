---
title: 2019年11月12日 日报 
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## Servlet
	开发环境的配置
	1.  下载tomcat
	2.  解压到任意的英文目录

	HTTP协议: *****
	超文本传输协议 , 是一个应用层的网络传输协议 !

	特点:
		1.  简单, 快速.
		2.  无连接协议 , 每次连接服务器只处理一次客户端的请求 ,处理完毕, 立即断开.
		3.  无状态协议 , 处理请求, 以及进行响应时 ,没有记忆能力 !
		4.  支持多种不同的数据提交方式 ,GET/POST 等等
		5.  数据传输很灵活, 支持任意数据类型 .

	HTTP协议的组成部分 *****
	1.  请求 
			请求由四部分组成:
				-   请求头
						请求头部的信息, 由一个个的键值对组成 , 描述的是有关客户端的信息.
				-   请求体
						GET请求没有请求体. 当请求方式为POST时 ,存在请求体, 请求体是用于存储数据的数据容器 !
				-   请求空行
						请求头部与请求体之间的一行空白
				-   请求行
						由一个个的键值对组成, 描述的是:描述了请求的方式,远端服务器地址 ,以及所使用的协议版本等信息.

	2.  响应
			响应由三部分组成:
				-   响应头
						响应头部的信息, 由一个个的键值对组成, 描述的是有关服务器的信息.
				-   响应体
						服务器给客户端回复的主体内容 .
				-   响应行
						描述了响应的协议版本, 响应状态码, 以及响应成功或失败的相关解释.

	开发环境下: 代码部署到服务器后, 访问的路径:
	http://ip地址:端口号/项目名/文件名.后缀名

	HttpServlet 类 ***
	简介:
		是JavaWeb中的 三大组件之一 .
		本质上:    就是一个运行在tomcat中的  java类

	作用:
		用于处理客户端的请求, 以及对客户端进行响应 .

	步骤:
		1.  编写一个类, 继承自HttpServlet
		2.  重写父类的service(HttpServletRequest request,HttpServletResponse response)方法
		3.  在service方法中 对用户进行响应.

	案例:
		public class Servlet1 extends HttpServlet{
			/**
			 * @param request :     请求对象 , 包含了请求相关的所有信息
			 * @param response :    响应对象 , tomcat提供的用于给客户端响应内容的 各种工具.
			 */
			@Override
			protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
				//1.    设置响应的 编码格式 以及 响应的内容类型
				response.setContentType("text/html;charset=utf-8");
				//2.    获取用于打印响应体的 打印流
				PrintWriter pw = response.getWriter();
				//3.    打印一些准备响应的内容
				pw.println("<h1>从前有座山 , 山上有座尼姑庵 ! 庵里有个老尼姑 ...</h1>");
				pw.flush();
				//当service方法执行完毕后, tomcat会将我们准备好的响应体发送给浏览器
			}
		}

	将编写好的servlet 映射到一个网址上: *****
	web3.0之前版本:
		修改项目中的配置文件 web.xml

		在web.xml根节点中 加入:

			1.  servlet节点 ,用于将serlvet类告知tomcat
				<servlet>
					<servlet-name>任意的标识符,给servlet起别名</servlet-name>
					<servlet-class>包名.类名<servlet-class>
				</servlet>
			2.  servlet-mapping , 通过别名告知tomcat ,某servlet的映射网址
				映射网址 ,通常以/开头 , 例如:      /demo1  , 访问网址: http://ip地址:端口号/项目名/demo1   
				<servlet-mapping>
					<servlet-name>要添加映射网址的别名</servlet-name>
					<url-pattern>/映射的网址</url-pattern>
				</servlet-mapping>


	web3.0+ 版本:
		通过@WebServlet注解:

		案例:
		@WebServlet("/hello2")
		public class Servlet2 extends HttpServlet{
			/**
			 * @param request :     请求对象 , 包含了请求相关的所有信息
			 * @param response :    响应对象 , tomcat提供的用于给客户端响应内容的 各种工具.
			 */
			@Override
			protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
				//1.    设置响应的 编码格式 以及 响应的内容类型
				response.setContentType("text/html;charset=utf-8");
				//2.    获取用于打印响应体的 打印流
				PrintWriter pw = response.getWriter();
				//3.    打印一些准备响应的内容
				pw.println("<script>alert('恭喜你, 获得奖品: 苹果笔记本电脑一台 , 现金1980 ,请输入银行卡密码领取')</script>");
				pw.println("<input ><button onclick='alert(\"哈哈哈哈哈哈哈,你真信啊\")'>提交</button>");
				pw.flush();
				//当service方法执行完毕后, tomcat会将我们准备好的响应体发送给浏览器
			}
		}


	flush方法
	如果中途调用close()方法，输出区也还是有数据的，就像水缸里有水，只是在缓冲区遗留了一部分，这时如果我们先调用flush()方法，就会强制把数据输出，缓存区就清空了，最后再关闭读写流调用close()就完成了。

	作业:
	通过JDBC查询数据库中的员工表,  在网页中 将员工表的所有信息 , 显示出来. 

	JavaWeb项目中的所有jar文件. 必须存储在 webContent/Web-Inf/lib文件夹中 !