---
title: 2019年10月10日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---
## java01       
      初次打印:
        //导入java目录中的util目录中的scanner类
        import java.util.Scanner;
        public class Java01{
                public static void main(String[] args){
                        System.out.println("打印,打印");
                }
        }
        public/*代表是公开的*/ class/*是类*/  java01/*是类名,要与文件名一致*/{

        /*类体*/
                public static void main/*主方法名,是程序的入口*/(String[] args){
                                /* String是字符串类型*/
        String name;
        int age;
        /*方法体*/
        System.out.println("请输入年龄");

        //创建一个扫描器对象负责扫描键盘的输入
        Scanner sc=new Scanner(System.in);
        //从键盘输入中读取一个字符串内容放入name变量对应的变量中
        nane=sc.next();
        //从键盘输入中读取一个整数放入age变量对应的内存空间中
        age=sc.nextInt();

        //打印
        system.out.println("name="+name);
        system.out.println("age="+age);
        }
        }

        注释:
        多行注释:/**/
        单行注释://
        java语言的特性:
        编写java的流程
        1.新建一个记事本,命名为xxx.java
        2.切换dos窗口,切换到上述.java文件所在的目录
        3.使用javac  xxx.java 进行编译生成字节码文件.class
        4.使用java  xxx进行解释并执行字节码文件
        特性:
        (1)java语言是一门纯面向对象的编程语言。
        (2)java语言编写的代码具有跨平台特性，也就是说使用javac将java代码翻译成
        字节码文件之后，由于不同的操作系统中都拥有不同的java虚拟机分别进行解释，       从而可以得到不同平台的机器码，因此得到了"一次编译，到处运行"的美名。(java的跨平台原理)
        (3)java虚拟机拥有自动垃圾回收机制，也就是内存空间的释放。


        java编写注意事项:
        1.类名中每个单词的首字母都要大写
        2.每个部分之间用空行隔开
        3.要有空格和缩进
        4.变量名由多个单词组成时,从第二个单词的首字母开始大写
        5.变量名区分大小写