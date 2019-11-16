---
title: 2019年11月15日 日报 
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## Servlet
	HttpServletRequest类的常用操作:
	1.获取访问客户端ip地址
	String ip=request.getRemoteAddr();
	2.获取客户端访问的地址(有可能因为服务器映射了多个域名,多个用户的访问地址不同)
	request.getRequestURI();
	3.获取服务器的名称(通常获取的是IP地址)
	request.getServerName();
	4.获取端口号
	request.getServerport();
	5.获取请求的方式
	String method=request.getMethod();
	6.获取get请求的参数列表(网址中?后边的部分)
	String params=request.getQueryString();
	三个将请求对象作为数据容器使用的方法:
	1.存储数据
	request.setAttribute(String key,Object value);
	2.获取数据
	Object value=request.getAttribute(String key);
	3.删除数据
	request.remoAttribute(String key);


	ServletContext 上下文
	每一个Servlet都是一个独立的用于处理请求的对象,
	为了便于多个Servlet之间的数据交流,javaweb提供了一个上下文对象
	我们在任何的Servlet代码中都可以获取这个ServletContext对象,且每一个Servlet获取的都是同一份ServletContext对象
	上下文对象类似于我们SE中学习的MAP集合,是一个键值对的容器,

	作用:ServletContext是Servlet之间通信的桥梁,用于多个Servlet之间信息的共享
	如何在Servlet中得到上下文对象:
	格式:
	ServletContext context=getServletContent();
	ServletContext的常用方法
	1.存储数据
	context.setAttribute(String key,Object value);
	2.获取数据
	Object value=context.getAttribute(String key);
	3.删除数据
	context.remoAttribute(String key);
	4.获取项目运行时的文件夹绝对路径
	String puth=context.getRealPath("/");
	//因为一个项目只有一个ServletContext对象,且在项目启动的时候就创建了,项目销毁时销毁,
	//所以一次项目启动的过程中,一个Servlet存储的数据,任何Servlet都可以获取到,


	会话跟踪(状态管理)
	HTTP协议是无状态的,我们的服务器与客户端进行交互时没有记忆.
	两种方式来实现状态管理:
	1.Cookie技术:将状态存储到客户端中
	2.Session技术:将ID存储在客户端中,将状态存储在服务器中.
	Cookie技术
	技术实现步骤及原理:
	1.当服务器向客户端响应数据时,可以向相应头部加入cookie,每一个cookie表示一个键值对.
	2.浏览器在接收到相应后,如果存在cookie则会将cookie存储在文本文件中(.txt)
	存储时,存储的信息有:服务器的域,路径,Cookie存储的键和值,存储的时长...
	3.当浏览器向客户端请求时,会遍历Cookie的文本文件,将匹配新请求地址的Cookie携带上放在请求头部发送给服务器
	Cookie匹配的规则:
	当Cookie存储的域相同时,路径匹配时,才会将Cookie发送给服务器
	只允许存储字符串,不允许存储中文
	如何创建Cookie
	Cookie在java中的体现就是一个表示键值对的java类,类名为:Cookie 
	格式:
	Cookie cookie=new Cookie(String name,String value);
	如何将Cookie添加到相应头部
	通过响应对象将Cookie添加到响应头部
	格式:
	response.addCookie(Cookie cookie);
	一次响应可以添加n个Cookie
	如果浏览器中已经存储过某个Cookie的name相同的Cookie,再次存储时会覆盖value

	如何从请求头部得到之前的所有Cookie
	因为一个域和路径下,可能存在多个Cookie,所以获取的不是单个Cookie而是Cookie数组:
	Cookie[] cookie=request.getCookie();
	//如果从未存储过返回的数组值是null
	得到Cookie后,如何取出其中的键和值
	获取Cookie的键
	String name=Cookie.getName();
	获取Cookie的值
	String value=Cookie.getVlues();
	如何调整Cookie存储时长
	cookie.setMaxAge(int 秒);
	传入的值:	
	负数 : 默认值-1,表示浏览会话结束时,删除cookie
	整数: 存货的秒数,例如:60*60*24*365*10表示十年
	0	经常用于覆盖一个cookie时使用,作为0秒后删除(立即删除)
	Cookie存储时,路径问题的解决,
	路径匹配的规则:
	Cookie的替换:只能由相同域,相同路径的响应来完成替换
	Cookie的获取:
	例如:
	A地址: localhost/x/a.do
	B地址: localhost/x/b.do
	C地址: localhost/c.do
	A存储数据时:a和b可以获取,a和b可以替换.c不能获取也不能替换
	C存储数据时:a/b/c可以获取,c可以替换
	Cookie的路径问题,经常影响我们的开发
	Javaweb给我们提供了一个Cookie的方法,用于设置Cookie的路径.
	通常我们会将Cookie的路径设置为/(根路径)
	推荐使用:格式:cookie.setPath("/");
	Cookie优缺点:
	缺点:
	1.Cookie存储的数据类型有限制,只能是字符串
	2.数据存储的大小有限制,最大为4kb
	3.数据存储在用户的计算机上不安全
	4.受限于用户浏览器的限制,当浏览器进制使用Cookie时,Cookie就无法再存储了.
	优点:
	数据存储在客户端,分散了服务器的压力

	Session技术(会话)
	基于Cookie实现的技术,是java中的键值对的容器,就像我们常用的Map集合.
	技术原理:
	1.浏览器访问服务器时,服务器可以选择创建session对象.
	2.session对象在创建时,会生成一个id,我们称其为sessionid,sessionid是session的密钥,是唯一的
	3.session创建完毕后,会自动将session以cookie的方式存储到用户的浏览器中
	4.浏览器再次访问服务器时,会自动携带sessionid发送给服务器
	5.服务器得到sessionid后,会去匹配找到对应的session对象
	如何获取session对象
	在Java中,session是一个Java对象,对象的类型为HTTPSession
	创建Session对象的格式:
	格式1:无参方法:
	HttpSession session=request.getSession();
	内部调用了,一参方法,且传入true
	格式2:一参方法:
	HttpSession session=request.getSession(boolean isNew);
	用于获取session参数
	true:根据当前浏览器传入的sessionid,寻找session对象并返回,如果不存在则创建新的session
	false:根据当前浏览器传入的sessionid,寻找session对象并返回,如果不存在则返回null
	Session的常用方法
	1.存储数据
	session.setAttribute(String key,Object value);
	2.获取数据
	Object value=session.getAttribute(String key);
	3.删除数据
	session.removeAttribute(String key);
	4.销毁session(应用场景:99%情况是退出登录)
	session.invalidate();
	Session的存活时长以及调整:
	session默认时长:30分钟
	指的是:距离用户的上一次访问大于30分钟后,session自动删除
	设置session时长:
	方式1:修改单个session的时长:
	session.setMaxInactiveInterval(int 秒);
	方式2:修改tomcat下所有session的默认时长
	独立环境:寻找到config文件夹中的web.xml配置文件
	开发环境:寻找到Servers项目中的tomcat文件夹下的web.xml
	修改web.xml中的session-config节点
	<session-config>
	<session-timeout>数值</sessiout-timeout>
	</session-config>
	Session优缺点:
	优点:
	1.数据存储在服务器中,安全
	2.session存储时的值类型是Objec(万物)可以存储任何类型的数据
	3.可存储的数据大小理论上是无上限的
	缺点:
	存储数据在服务器的内存中存储.内存通常是有限的,会给服务器造成大量的压力,很容易耗尽服务器资源
	注意:Cookie技术和session技术不是互斥的
	cookie和session是结合使用的
	通常:
	对于安全不敏感的数据,建议使用cookie存储
	对于安全敏感的数据,建议使用session存储
	对于安全敏感的,且较大的数据,存储在数据库
	Seesion和cookie的区别:













