---
title: 2019年9月23日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---
## ES6
 wind.onload是让整个页面加载后执行
document.querySelector("css元素");获取元素
document.getElementById('li).appendChild(文本');  添加一个li标签在所有li的后边，内容是文本
var list=document.getElementById("li")list.insertBefore(newItem,list.childNodes[0]);添加一个li标签在所有li标签的前面
定义变量有两种方法：
let和const
let是变量相当于js中的var
const是常量
这两个属于是块级作用域(大括号中就属于一个块)
    {
        let a = 1;
        console.log(a);
        {
            let a=2;
            console.log(a);
        }
    }
var与let及const的区别
var：只在函数和全局中有作用域的说法，在if或for中没有
let和const：在if或for中也有作用域的说法，在if和for中声明了也就只能在这个for中使用
如果在一个函数外定义了变量a在函数中又定义了函数a就要看函数中定义的a在函数中的位置，如果是先赋值后做动作就使用函数中赋的值，如果在动作之后就会报错
let注意：
1.没有预解析，就是在一个函数当中将动作写在赋值前面，动作中使用的变量将会显示不被定义错误
先定义再使用
例子<script>
    let a=12;
    function fn(){
        alert(a);//TDZ 暂时性死区 开始
        let a= 5;//TDZ 暂时性死区 结束
    }        
    fn()
</script>
2.let不能在同一个块中重复定义变量
3.分为父级作用域与子级作用域(看似重复定义变量，其实是不属于重复定义)
例1<script>
    for(let i = 0 ; i<10; i ++){//这里的i父级作用域
        let i = 'abc';//这里的i是子级作用域
        console.log(i)
    }
</script>
例2:<script>
    var arr = [];面刚加载完成后执行 

比如根据给元素设置初始值，
    for(let i = 0 ; i < 10 ; i ++){//这里使用var是不行的，因为var定义的是全局变量，下面的数组用i的时候给自己传参就不好用了
        arr[i]=function(){
            console.log(i);
        }
    }
    arr[5]();
</script>
const的特性：
1.const定义后是不能修改的
2.const定义时候必须赋值，不能后赋值  const a = 5;
3.const定义时候在不同的作用域，则可以重复定义，因为不在同一个作用域就不属于重复赋值
4.如果利用一个定义const常量为数组，利用push方法对数组中插入数组信息，是可以插入的，如果不想常量数组被修改可以使用Object.freeze(对象)进行对象冻结
<script>
    const a=Object.freeze(['aaa','bbb']);
    console.log(a);
</script>
ES6的建议：以后就使用let了不要去使用var

解构赋值：
非常重要，特别在数据交互的时候，ajax
可以将多个变量同时赋值
注意：左右两边的解构和格式要保持一致
<script>
    let [a,b,c]=[1,2,3];
    console.log(a,b,c);
</script>
或
<script>
    let [a,[b,c]]=[1,[2,3]];
    console.log(a,b,c);
</script>
也可以给默认值
<script>
    let [a,b,c='暂无数据']=[1,2];
    console.log(a,b,c);
</script>
也可以将对象中的东西都直接赋值给各个变量
<script>
    let qp={  
        name:'ff',
        age:18,
        sex:'men'
    };
    let  {name,age,sex} = qp;
    console.log(name,age,sex);
</script>
或
<script>
    let qp={  
        name:'ff',
        age:18,
        sex:'men'
    };
    let  {name,age,sex:a} = qp;
    console.log(name,age,a); 
</script>
这时候输出的地方就不能写sex，只能写a，相当于给sex改名

例:将a和b的值进行互换
<script>
    let a =12 ;
    let b =1;
    [a,b]=[b,a];
    console.log(a,b);
</script>


函数中的数值选择性的输出
<script>
function run(){
  return{  
      name:'ff',
        age:8
        }
}
({name,age}=run());面刚加载完成后执行 

比如根据给元素设置初始值，
console.log(name,age)
</script>

字符串模板（可以随意的换行）
使用``就不需要进行字符串拼接了，
<script>
    let name='ff';
    let age=8;
    console.log(`这个女人叫${name},今年${age}岁`)
</script>
查看字符串长度：
    let a='123123';
    if(a.indexOf('123123')!=-1){
        alert(true);
    }else{
        alert(false);
    }


查找文本：
indexOf返回要找东西的索引位置，includes返回的是布尔值

判断一个字符中是否有一个字符
<script>
    let a='123123'; 
    alert(a.includes(1))
</script>
字符串以什么开头或什么结尾
str.startsWith(要检测的东西)
str.endsWith(要检测的东西)

填充字符串
str.padstart(整个字符串长度.填充的东西)往前填充
str.padEnd(整个字符串长度.填充的东西)往后填充
函数：
函数默认参数：（方法有多个，可以查文件）
   <script>
        function show({x=0,y=0}={}){
            console.log(x,y);
        }

        show()
    </script>
2.函数从参数默认已经定义了，不能再使用let,const声明
3.扩展运算符、reset运算符：
...三个点
在输出时候可以展开数组输出 显示数组中的各个值
console.log(...数组名);

function show(...a){
console.log(a);
}
show(1,2,3,4,5);
输出：1,2,3,4,5

打印剩余参数给最后的参数，三个点必须在最后一个参数上
<script>
    
        function run(a,b,...c){
            console.log(a,b,c)
        }
        run(1,2,3,4,5,6)
</script>

箭头函数 =>
<script>
  function show(){
      return 1;
  }
  console.log(show());
</script>
等价与
<script>
  let show=()=>1
  console.log(show())
</script>
写语句的话如下：
<script>
  let show=(a,b)=>{
        return a+b;
  }
  console.log(show(1,3));
</script>
注意：
1.this问题与js中的this不一样，是定义函数的时候所在的对象，不再是运行时候所在的对象了
2.箭头函数里面没有arguments,用...三个点
3.箭头函数不能当构造函数
数组：
ES5里边的一些东西
循环：
1.for
2.while
arr.forEach()
arr.map()
arr.filter()
arr.some()
arr.every()
arr.reduce()
arr.reduceRight()


使用arr.forEach()遍历
<script>
 let arr=[1,2,3,4,5];
 arr.forEach(function(val,index,arr){
            console.log(val,index,arr);
        })
</script>
其中arr.forEach/map可以接受两个参数
arr.forEach/map(循环回调函数,this指向谁);
arr.map()   非常有用，做数据交互 ”映射“
正常情况下配合return，返回是一个新的数组若没有return，相当于forEach
若是没有return，相当于forEach
注意：平时只要用map一定要有return
<script>
let arr=[
    {title:'aaa',read:100,hot:true},
    {title:'bbb',read:100,hot:true},
    {title:'ccc',read:100,hot:true},
    {title:'ddd',read:100,hot:true}
]
let newarr = arr.map((item,index,arr)=>{
    let  a={}
    a.t=`:-D${item.title}-----`;
    a.r=item.read+200;
    a.hot=item.hot==true && '真棒！！！';
    return a;
})
console.log(newarr);
</script>
arr.filter()过滤，如果return返回是true就留下，
<script>
let arr=[
    {title:'aaa',read:100,hot:true},
    {title:'bbb',read:100,hot:true},
    {title:'ccc',read:100,hot:true},
    {title:'ddd',read:100,hot:true}
]
let newarr = arr.filter((item,index,arr)=>{
    return item.hot==true;
})
console.log(newarr);
</script>
arr.some 看数组中有没有对应的值，如果有就返回ture 
every:一假即假:
some:一真即真 
参数 描述
val 必须。当前元素的值
index 可选。当前元素的索引值
arr 可选。当前元素属于的数组对象
<script>
let arr=['a','b','c']
let newarr=arr.some((val,index,arr)=>{
    return val=='a';
})
console.log(newarr);
</script>
arr.reduce(前一个数，当前的数，键值，数组)=>{

}
<script>
    let a =[1,2,3,4,5,6,7];
    let b = a.reduce((prev,cur,index,arr)=>{
        return prev+cur;
    });
    console.log(b);
</script>
for of遍历
const fruits = ['apple','coconut','mango','durian'];
fruits.fav = 'my favorite fruit';

//ES6中的for...of循环，遍历属性值
for(let fruit of fruits){
    console.log(fruit);
}

//支持终止循环，也不会遍历非数字属性
for(let fruit of fruits){
    if(fruit === 'mango' ){
        break;
    }
    console.log(fruit);      //apple coconut durian
}
for of遍历
<script>
    let arr = [1,2,3,4,5];
   
    for(let b of arr){
        console.log(b);
    }

</script>

对象：
对比两个变量一不一样
object.is(变量1,变量2)
语法:
		let promise = new Promise(function(resolve, reject){
		    //resolve,   成功调用
		    //reject     失败调用
		});

		promise.then(res=>{       //then就是在promise中添加解决和拒绝状态的回调函数

		}, err=>{
			
		})


	promise.catch(err=>{})
<script>
let a =1;
let b = new Promise(function(cg,sb){
    if(a==10){
        cg('成功');
    }else{
        sb('失败')
    }
});
b.then(sb=>{
    console.log(res);
},err=>{
    console.log(err)
})
</script>

模块化：必须在服务器环境下
<script type='module'>
      
</script>
定义模块：export 定义的东西
引用模块：inport 路径
注意：引用需要服务器环境	
特点：
1.import可以是相对路径，也可以是绝对路径
2.import模块只会导入一次，无论你引用多少次
3.import ‘路径’;如果这么用，相当于引用文件
