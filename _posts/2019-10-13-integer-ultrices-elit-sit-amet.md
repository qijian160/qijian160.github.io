---
title: 2019年10月13日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---
## java    
    分支
        if语句
        语法格式:
        if(表达式){
        语句块1;
        }else{
        语句块2;
        }
        语句块3;
        或
        if(表达式){
        语句块1;
        }else if(表达式){
        语句块2;
        }else{
        语句块3;
        }
        语句块4;
        switch语句:
        语法格式:
        switch(变量/表达式){
        case 字面值1:语句块1;break;
        case 字面值2:语句块2;break;
        default:语句块3;
        }
        语句块4;
        注意事项:
        switch()中可以是变量也可以是表达式,但必须是byte类型,short类型,char类型以及int类型,从jdk1.5开始支持枚举类型的,从jdk1.7开始支持string类型
        循环
        for循环
        语法格式:
        for(表达式1;条件表达式;表达式2){
        循环体;
        }
        语句块;
        关键字:
        break和continue
        break:跳出当前结构,执行后续代码,break的外围可以使循环也可以是switch语句
        continue:表示结束本次循环,进行下一次循环,continue外围必须是循环
        break如果在嵌套循环中,有多层循环,就要给外层循环一个标号,要跳到哪个循环外
        这里的a就是标号
        a:for(...){
        for(...){
        break a;
        }
        }
        无限循环:死循环
        for(;;){
        ...
        }
        双重循环:
        语法格式:
        for(表达式1;条件表达式;表达式2){
        for(表达式1;条件表达式;表达式2){
        循环体;
        }
        }
        注意事项:
        1.外层循环变量动一下,则内部循环变量跑以一圈
        2.当需要打印多行多列数据的时候,可以使用双重for循环
        whlie循环:
        语法格式:
        while(表达式){
        循环体;
        }

        while和for的比较
        whlie和for循环是可以完全互换的
        while(true)相同与for(;;)
        while循环主要用于明确循环条件不明确循环次数的场合
        for循环主要用于明确循环次数或范围的场合
