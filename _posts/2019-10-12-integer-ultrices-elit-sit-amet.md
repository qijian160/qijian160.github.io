---
title: 2019年10月12日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---
## java03      
        1.常用运算符
        1.1算数运算符
        + - * / %
        运算时候如果两个int型运算后想得到小数型的,可以如下操作:
        进行强制类型转换:
        System.out.println((double)5/2);
        这样5就会被转换成double型,结果是2.5
        System.out.println((double)(5/2));
        这样结果就是2.0
        System.out.println(1.0*5/2);
        这样也会先把5转成double型
        0不能做除数
        1.2关系运算符
        >	  <	!=	 >=	  <=  	==	

        笔试题:
        i==2 //判断i是否等于2
        2==i	//判断2是否等于i
        i=2// 将2赋值给i
        2=i	报错
        1.3自增自检运算符
        ++和--
        建议:不要将++或--与其他运算符一起使用,建议单独使用,也不要在同一个表达式中多次修改同一个变量的数值
        1.4逻辑运算符:
        &&表示与运算
        ||表示或运算
        !表示逻辑非
        ^表示异或

        短路特性:
        逻辑与运算时候,如果第一个为假,则不会看第二个
        逻辑或运算的时候,如果第一个为真,则不会看第二个
        1.5三目运算符
        语法:条件表达式:表达式1?表达式2;
        当条件表达式成立时,执行表达式1
        当条件表达式不成立时,执行表达式2
        1.6复合运算符
        +=  -=  *=  /=
        笔试题:byte ia=ia+5  和ia+=5的区别
        byte ia=ia+5
        编译报错,因此需要强制转换
        ia+=5
        编译通过,等价于ia=(byte)(ai+5)
        1.7字符串连接符:
        +表示字符连接符
        当+两边的操作数都不是字符串时会按着算数运算符的规则运算.
        当+两边的操作数只要有一个是字符串时,就按着字符串连接符的规则进行运算
        例子:
        ia是1  ib是2  ic是3
        System.out.println("结果是:"+ia+ib+ic);//结果是:123
        System.out.println(ia+ib+ic);//6
        System.out.println("结果是:"+(ia+ib+ic));//结果是:123
        System.out.println(""+ia+","+ib+ic);//1,23
        System,out,oruntln(1+2+"是结果")//3是结果

        1.8运算符的优先级:
        1.()的优先级最高
        2.=的优先级最低
        3.*/%同级
        4.+-同级