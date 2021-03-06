---
title: 2019年10月18日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---
## java
    今日内容:
		(1)面向对象编程的概念
		(2)类和对象以及引用
		(3)成员方法

		1.什么是对象?
		万物皆对象
		2.什么是面向对象?
		面向对象就是指以特征(属性)和行为的观点去分析现实世界中事务的方式
		3.什么是面向对象编程?
		面向对象编程就是指先使用面向对象的方式进行分析,再使用任意一门面向对象的编程语言进行翻译的过程
		面向对象里面的内容还是用面向过程写的
		例子:
		洗衣服:如果面向对象,我就把衣服交给洗衣机自动洗
		如果面向过程,我就要把衣服自己洗完
		4.如何学好面向对象编程?
		深刻理解面向对象的三大特征:封装,继承,多态.


		对象开始:
		1.类,对象以及引用(抽象,难点,重点)
		2.1对象和类的概念:
		对象是客观存在的实体,在java语言中体现为,内存空间的一块区域
		类就是分类的概念,是对具有相同特征和行为的多个对象的抽象描述,在java语言中包含描述特征的成员变量和描述行为的成员的方法,类是创建对象的模板
		类例子:
		string name="何杰"; 
		int age=18;......
		这时候要在声明一个人
		string name="小明";
		int age=17;.....
		又来一个人
		string name="天凯";
		int age=16;.....
		...........
		这样就很麻烦,但是我们可直接定义一个人类的类,
		人类:
		特征:姓名,年龄
		行为:学习,吃饭

		类:
		定义语法格式:
		class 类名 {
		类体;
		如:
		成员变量:		
		数据类型  成员变量名=初始值;     其中-初始值省略,但分号不能省略
		}
		如:
		class Person{
		string name;
		int age;
		}

		注意:
		类名:当类名由多个单词组成时,每个单词首字母都要大写;
		成员变量名:由多个单词组成的时,从第二个单词开始每个单词首字母大写;
		类不能干活,所以就得在类中创建对象
		 扩展:
		局部变量:主要在方法体中声明,作用范围从声明开始到方法结束
		成员变量:主要在方法体外,类体内声明的变量,作用范围从声明到类体结束


		对象:
		当一个类定义存在后,可以使用new运算创建该类的对象,对象创建的过程一般称为实例化
		对象的创建:
		new 类名();
		如:
		new person();
		创建一个person类型的对象,由于此对象没有名字因此叫做"匿名对象"
		注意事项:
		1.当一个类定义完毕后,使用new关键字创建对象的过程我们叫做实例化
		2.当创建对象的本质就是在内存空间的堆区申请存储空间,来存放该对象独有的特征信息.
		引用:
		基本概念:
		在java语言中使用引用数据类型声明的变量我们就叫做引用型变量,简称为"引用"
		引用主要用于记录对象在堆区中的内存地址信息,便于下次访问语法格式:
		类名 引用变量名 ;
		如:
		person p;  表示声明person类型的引用变量p,本质上在栈区申请存储空间
		person p=new person();  表示声明引用变量p来记录persno类型对象的地址信息
		这样p在栈区中,person类在堆区中,引用变量p的栈区与person类的堆区形成了联系,这样就可以访问类中的特征了
		利用引用变量p去访问person类中的成员变量:
		引用变量名.成员变量名;
		如:
		p.name="小明";表示使用引用变量p访问所指向堆区对象的姓名特征

		引用类型:
		除8种基本类型外,用类名声明的变量称为引用类型变量,简称引用

		类的定义和使用: 当一个成员变量没有初始化赋值的情况下,它的值就是null
		public class Int{     //声明了Int类
			String name;  //成员变量定义为name和age两个
			int age;
			public static void main(String[] agrs){  //程序入口
					Int p = new Int();   //对引用变量p进行实例化,
					p.name="q";	//引用变量p访问堆区中的name成员变量并赋值
					p.age=18;	//引用变量p访问堆区中的age成员变量并赋值
					System.out.print(p.name);
					System.out.print(p.age); 
				}
			}

		成员方法:
		语法格式:
		class 类名{
		返回值类型 成员方法名 (形参列表){
		成员方法体;
		}
		}
		如:
		class person{
		String name(){
		System.out.print("fff");
		}
		}
		格式详解:
		1.返回值类型:
		在方法体中使用return关键字返回数据内容,并结束当前方法
		如返回的内容是66时候,就是 return  66;
		从方法体内向方法体外返回的内容我们叫返回值;
		返回值类型可以使基本数据类型也可以是引用数据类型
		如:
		当返回值数据内容是66时,则返回值类型是int型即可;
		当返回的数据内容是3.14时,则返回值类型是double型即可;
		2.void,如果当前方法不需要返回任何数据内容,则返回值类型写void即可
		3.形参列表:形式参数主要用于,将方法体外的数据传入到方法体的内部.
		语法格式:数据类型 形参名
		形参列表就是指多个形式参数组成的整体
		语法格式:数据类型 形参名1,数据类型 形参名2,......
		若方法不需要传入任何数据内容,则形参列表位置啥也不写
		4.成员方法体
		成员方法体主要编写描述该方法功能的语句
		如:
		该方法的功能就是打印,方法体内的代码应该是System.out.print(....);
		当该方法的功能就是返回66时,方法体内的代码应该是return 66; 
		成员方法例子:
		public class Int{
			int a(int b,int c){
				return b+c;
			}
			public static void main(String[] agrs){
				Int p = new Int();
				System.out.print(p.a(1,3));
			}
		}

		方法的调用:
		语法格式:
		引用变量名.成员方法名(实参列表);
		如:
		p.show(); 使用引用变量p调用show方法
		例子:
		public class Int{
				String name;
				int age;
				void  a(){
					System.out.print(name+age);
			}
				public static void main(String[] agrs){
				Int p=new Int();
				p.a();
				p.name="qq";
				p.age=18;
				p.a();
			} 
		}
		注意:
		1.实参列表:主要用于对形参列表进行初始化操作,因此参数的个数,类型,顺序都必须和形参保持一致
		2.实参可以传递直接量,变量,表达式以及方法的调用等;

