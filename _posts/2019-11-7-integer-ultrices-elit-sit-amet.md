---
title: 2019年11月7日 日报 
teaser: 十多天的努力
tags: [markdown, workflow, foss]
---
## java学习经过了好几天,最终以在线考试系统收尾
    项目的问题:
		1.使用io流时要注意传输数据的类型,如writeobject和readobject只能读写对象
		2.序列化问题
		3.io流一一对应
		4.类型强制转换List<TestQuestionMessage> tqml=(List<TestQuestionMessage>)bi.readObject();
		5.碰到远程序列化错误就去修改序列化码,服务器端和客户端必须相同
		6.当将集合向文件写入的时候要先写入一个空集合再进行读写将对象写入集合再放入文件中
	项目中熟练使用IDEA操作
		每日分享->idea 自定义设置
		内存显示以及性能优化
		Preferences–>Appearance & Behavior–>Appearance，右侧勾选Window Options下面的Show memory indicator即可
		安装目录中的bin文件夹->idea64.exe.vmoptions-> 前两行 最大内存 最小内存 16GB 建议 把idea的最大内存设置2048m，最小内存1024m
		区分大小写
		Editor->General->Code Completion->取消Match case前的勾选
		软换行
		自定义折叠代码区域功能
		(用啥包裹代码块)
		更改变量名
		方式1 查找替换 方式2 alt+j 方式3 s+F6
		字体快速缩放
		Editor->General->Mouse->Change font size(Zoom)with Ctrl+Mouse Wheel
		显示调用处
		A+F7
		跳转定义位置
		C+b
		自动导包
		Editor->General->Auto Import add 自动优化导入的包
		去除没用的包
		C+A+o Editor->General->Auto Import->Optimize
		类结构
		TODO
		并行运行or重新运行
		配置运行方式 edit configurations
		统计代码量
		statistic插件
		IDEA中调试代码
		https://victorfengming.github.io/2019/10/jetbrains-idea-debug/
		强行假装git
		本地文件的历史记录 项目右键->Local History ->Show Hisory Put Label
		IDEA使用git
		https://blog.csdn.net/qq_40223983/article/details/102543484 https://victorfengming.github.io/2019/10/git-idea/
	报错处理:
		1.java.net.SocketException: Connection reset(一般是服务器和客户端运行之间,有一段关闭了,另一端就会报这个错误)
		2.Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: 1( for循环里面 i=3 然后还是递增的。。 你里面总共才3个数 最多也只有a.f[2]呀 ，就没有a.f[3])
		3.在用io流向文件中写入数据时,要看当前文件中存在的数据是否被序列化了,如果没序列化写入的新数据也不能序列化,如果写入序列化的数据与文件中的数据序列化状态不同,将报错
		4.遇到空指针,先缕思路,从报错处逐级向上查看,查看传值是否有断裂
		5.有一些错误不需要解决,直接重启IDEA