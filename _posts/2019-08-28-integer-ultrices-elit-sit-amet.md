---
title: 2019年8月28日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---

#### javascript
JS代码分为三个地方写：
    1.在script标签中写
        <script type='txt/javascript'></script>
    2.js代码可以写在h5标签中
    3.在js文件中可以写js代码，但是需要在html的页面中引用
        <script src='js文件路径'></script>
注释 // 单行注释     /*多行注释*/
alert('弹匡内容'); 如果不点击弹匡中的确定按钮则代码不会继续执行
js语法注意：
    1.js代码发生错误该错误的代码后面的js代码不会执行
    2.如果第一个对script标签中有错误不会影响后面的script代码执行
    3.script标签中可以加入type='txt/javascript'
    4.script标签在页面中可以出现多对
    5.script标签一般是放在body的标签最后的，有的时候会在head中(让其先加在html内容在进行js加载)
    6.如果script标签是引入外部js文件的作用，那么这对标签中不要写任何js代码，如果要写，重新写一对script标签，里面写代码
    7.js中字符串类型的值要用双引号或者单引号阔起来
    8.每行结束都要有分号
##### 变量：
    操作的所有数据都在内存中操作
    js中存储数据使用变量的方式
    js中生命变量都用ar
    存储数据应该有对应的数据类型
    变量名区分大小写

    变量声明(有var 有变量名字,没有值)
    变量初始化(有var 有变量名字,有值)
    变量声明的方式
        var 变量名
               例子：var number;
    也可以一次声明多个变量
        var 变量名，变量名，变量名；
     变量初始化(变量声明的同时并且赋值)
     存储一个数字10
        var number=10;
     存储一个名字
        var name='名字';
     存储真(true)
        var flag=true;
     存储一个空
        var nll=null;
     存储一个对象
        var obj=new object();
    变量名的注意问题：
        1.变量的名字要有意义
        2.变量名有一定的规范：一般可以字母，$符号，下划线开头，中间或后边页可以用
        3.变量名一般都是小写的
        4.驼峰命名法
        5.用拼音也要用驼峰的形式命名
console.log(变量名);将内容输出在浏览器的控制台中
js中数据类型：
        number,string,boolean(true false),null,undefined,object
        undefined(未定义状态：如果只是声明变量没有赋值给变量就会为此类型)
        如果一个变量的结果是undefined和一个数字进行计算，结果：NaN不是一个数字也没有意义
获取变量类型：typeof 变量名 或 typeof(变量名)
        例如：console.log(typeof 变量名)
进制表示：0数值 八进制   0x数值 十六进制
判断一个结果是不是NAN结果isNAN(数值或变量) 如果结果返回的是NAN代表此变量不是一个数字 
返回一个变量的字符长度是多少console.log(str.length)；
string类型：
        双引号不能嵌套双引号，单引号不能嵌套单引号，如果嵌套可以用转译符
        如果一个是字符串，另一个是数字，使用运算符可以将其转换为数字进行运算
字符串用+属于拼接
转换数值的三种方式：
        1.parseInt(变量或值);转成整数
               parseInt(10a); 结果：10
               parseInt(g10); 结果：NAN(遇见字符就停止)
        2.parseFloat(变量或值);转成小数
               parseInt(10a.98); 结果：10
               parseInt(g10.98); 结果：NAN(遇见字符就停止)
        3.Number(变量或值);转还成数值
               Number(10) 结果：10
               Number(1a0)结果：NaN
               这种方法比较严格，如果不是纯数字就会返回NaN
转换字符串类型
          1.tostring(变量或值)转字符串类型
          2.String(变量或值)
               如果变量有意义调用.tostring()转换    
                    例如：console.log(变量.tostring())
               如果变量没有意义使用String()转换
转换布尔类型
           boolean(值)；

##### 流程控制：
        分支：if(表达式){
                    }
               else{
                    }
        三元运算符：var 变量=表达式1?表达式2:表达式3；
        
        switch(表达式){
          case 值1:代码;break;
          case 值2:代码;break; 
         }
      循环结构：
            while(循环条件){
                循环体；           
            }
            do{
                循环体；
            }while(条件);
            for(起始条件;终止条件;影响条件){
                循环体;
               }
输入框 var 变量名=parseInt(prompt("请输入月份"));
break关键字可以跳出循环分支等
continue关键字直接跳到下一次循环
##### 数组：
数组的名字如果直接输出就可以直接把数组的数值显示出来
1.通过构造函数创建数组
语法：
var 变量名=new array(数组的长度);  最后括号中如果是一个数字就是数组的长度，如果数组中的多个数字就是数组的数据
2.通过字面量的方式创建数组
语法：
var arr=[];
3.定义数组
var arr=[];
arr[0]=值;
arr[1]=值；
arr[2]=值；
取数组长度
console.log(arr,length);
								进度:50%
