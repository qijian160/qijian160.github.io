---
title: 2019年10月19日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---
## java
     今日内容:
		1.构造方法和方法重载
		2.this关键字
		3.方法的传参和递归调用

		1.构造方法:(重点)
		构造方法概念:
		在一个方法中,如果出现类名与方法名相同的方法,这个方法就被称为构造方法
		如:person p=new person();
		这里的person方法就是构造方法
		语法格式:
		class 类名{
		类名(形参列表) {
		构造方法体
		}
		}
		如:在构造方法中对成员变量初始化,实参传入形参对初始值进行操作
		person(String n,int a){
		name=n;
		age=a;
		}
		特点:
		1.构造方法的名字与类名完全相同,没有返回值类型,连void都不许有.
		2.当使用new关键字构造对象时,会自动调用构造方法进行成员变量的初始化工作.
		默认构造方法:
		1.当一个类中没有自定义任何形式的构造方法时,编译器会自动添加一个无参的空构造方法,叫做默认或空构造方法	 如:person(){}
		2.若类中出现自定义构造方法,则编译器不再提供任何构造方法.
		3.有参构造和无惨构造可以同时存在,保证无参也可以不报错,在有参数的引用时就走有参构造,在无参数引用时就走无惨构造
		4.没有特殊要求,就要写两个方式的构造,一个是有参的一个是无参的
		构造方法例子:
		public class Person{
			String name;
			int age;
			Person(){
				name="qi";
				age=18;
			}
			Person(String n,int a){
				name=n;
				age=a;
			}
			void show(){
				System.out.println("我的名字是"+name+"今年我"+age);
			}
			public static void main(String[] agrs){
				Person p =new Person();
				p.show();
				Person e =new Person("qiqi",18);
				e.show();
			}
		}



		方法重载:
		1.基本概念:
		如果一个类中,如果出现方法名相同但参数列表不同这样的方法之间我们就构成重载关系
		2.体现形式:
		1.参数的个数不同
		2.参数的顺序不同
		3.参数的类型不同
		4.与参数变量名和返回值无关,返回值类型可以相同也可以不同,但建议返回值类型最好相同
		判断方法是否重载的核心;调用是否能区分
		3.实际意义:
		对于调用者来说,只需要记住一个方法名,就可以调用各种不同的版本,实现不同的效果.
		如:
		public class Person{
			String name;
			int age;
			Person(){
				name="qi";
				age=18;
			}
			Person(String n,int a){
				name=n;
				age=a;
			}
			void grow(){
				age++;
			}
			void grow(int i){
				age+=i;
			}
			void show(){
				System.out.println("我的名字是"+name+"今年我"+age);
			}
			public static void main(String[] agrs){
				Person p =new Person();
				p.grow();
				p.show();
				p.grow(9);
				p.show();
			}
		}

		this关键字
		基本概念:
		在构造方法中this关键字代表当前正在构造的对象
		在成员方法中this关键字代表当前正在调用的对象
		例子:
		public class Person{
				Person(){
					System.out.println("我是构造方法"+this);
				}
				void show(){
					System.out.println("我是成员方法"+this);
				}
			public static void main(String[] agrs){
				Person p = new Person();
				p.show();
			}
		}
		!!!!!在构造方法中出现了this,底下new给了谁,this就是谁
		!!!!!在成员方法中出现了this,谁引用了方法,this就是谁(这里就是p)
		public class Person{
				Person(){
				}
				Person(String n){
		System.out.println(n); //等价于System.out.println(this.n);等价于System.out.println(p1.n)或(p2.n);  
		//this等于q1或q2
				}
			public static void main(String[] agrs){
				Person p1 = new Person("q");
				Person p2=new Person("f");
			}
		}
		this的原理:
		当成员方法中访问成员变量时默认会加上this.(相当于汉语中"我的"),当不同的引用调用同一个成员方法时,会导致成员方法中的this不同,那么this.访问的结果随之也访问不同
		this关键字的作用:
		成员变量不能重名,局部变量不能重名,成员变量和局部变量可以重名,在局部变量的作用域之外,变量名代表成员变量,在局部变量作用域内,代表的是局部变量,如果想使用成员变量,需要使用this的方式访问.
		public class Person{
				String name;
				Person(){
				}
				Person(String name){
					this.name=name;  //这里的this.name等于p1.name或p2.name 
				}
				void show(){
					System.out.println(name);
				}
			public static void main(String[] agrs){
				Person p1 = new Person("q");
				p1.show();
				Person p2 = new Person("w");
				p2.show();
			}
		}
		this使用方式:!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
		1.当形参变量和成员变量同名时,在构造方法或成员方法中通常优先使用形参变量,若希望使用成员变量,就需要在成员变量名前加上this.进行说明.
		2.在构造方法中,可以使用this()调用本类的其他构造但要求this(实参)必须在本类的第一行
		例子:this()的例子
		public class Person{
				String name;
				Person(){
					System.out.println("无参构造");
				};
				Person(String name){
					this();
					System.out.println("有参构造");
				}
			public static void main(String[] agrs){
				Person p1=new Person("qi");
			}
		}
		this关键字空值的问题
		如果引用变量为空时,使用到了this关键字,则该关键字就会产生空指针异常的错误



		方法的传参和递归调用:
		基本概念:
		参数有形参有实参,基本数据类型参数时候,传输的就是值,如果是引用数据类型作为参数时,我们传输的就是地址
		要求掌握:
		1.当基本数据类型的变量作为方法的参数传递时,形参变量数值的改变不会影响到实参
		2.当引用数据类型的变量作为方法的参数传递时,形参变量指向的内容发生改变后会影响到实参变量指向的内容;
		3.当引用数据类型的变量作为方法的参数传递时,形参变量改变指向后再改变指的内容时不会影响到实参变量指向的内容;(在使用引用数组数据类型被引用方法时候,要想在形参改变的时候不影响实参就要在方法中执行之前再次声明一下数组,将数组的地址更改,否则实参和形参的数组地址是在同一个地址上,形参数据改变实参也会更新)


		gc垃圾回收机制:不断扫描堆区中的对象,看是否有人引用他,如果没有咋会被认为是内存垃圾就清理掉


		递归调用:
		基本概念:
		当一个方法体的内部调用当前方法自身的形式,叫做递归.
		注意事项
		1.方法自己调用自己
		2.递归可以大幅度简化代码
		3.递归要考虑性能问题,有些时候可以使用循环取代递归
		4.必须有退出条件
		5.必须使问题便简单,而不是复杂
		案例:
		自定义成员方法实现参数n阶乘的计算并返回
		递推方法:
		public class Person{
				int num=1;
				int show(int a){
					for (int i=a;i>0;i--){
						num*=i;
					}
					return num;
				}
				public static void main(String[] agrs){
					Person p = new Person();
					int b=p.show(5);
					System.out.print(b);
				}
		}
		递归方法:
		判断出阶乘就是n*n-1的结果
		public class Person{
			int show(int a){
				if(a==1){
					return 1;
				}
				return a*show(a-1);
			}
			public static void main(String[] agrs){
				Person p=new Person();
				int b=p.show(5);
				System.out.println(b);
			}
		}

		!!!!类方法类文件可以和入口代码文件分离,当在执行入口文件的时候遇到构造函数的实例化过程时,它就会在本目录下搜索本方法类的文件(就是new的类型,找与类名一致的文件名)











