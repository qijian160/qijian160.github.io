---
title: 2019年9月17日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---

#### VUE训练
  ```
CDN外联VUE 
<script src="https://cdn.staticfile.org/vue/2.4.2/vue.min.js"></script> 


VUE打印变量
<!DOCTYPE html> 
<html lang="en"> 

 
<head> 
    <meta charset="UTF-8"> 
    <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
    <meta http-equiv="X-UA-Compatible" content="ie=edge"> 
    <title>Document</title> 
    <script src="https://cdn.staticfile.org/vue/2.4.2/vue.min.js"></script> 
</head> 

 
<body> 
    <div id="ww"> 
        <p>{{name}}</p> 
        <p></p> 
        <p></p> 
    </div> 

 
 
    <script> 
        var nn = new Vue({
            el: '#ww',    //参数为需要获取的元素  html中的根容器元素
            data: {        //用于数据的存储
                name: '123',

 
            }
        })
    </script> 
</body> 

 
</html> 
所有要显示的内容必须在选择的元素下


定义方法（函数）
var nn = new Vue({
    el:'#ww',
    data:{
        name:'小阳阳',
    },
   methods:{
       pp:function(text){
           return  text +this.name;//这里实现了下面方法中的值与上面变量的值可以直接调用，进行拼接输出
       }
   }
});

VUE为标签绑定属性的方法
HTML文件：    
<div id="ww"> 
        <p>{{name}}</p> 
        <p>{{pp('你好')}}</p> 
        <p></p> 
        <a v-bind:href="link">百度</a> 
    </div> 

  
js文件 
 
        name:'小阳阳',
        link:'www.baidu.com' 

  

VUE绑定事件
    <button v-on:click='age++'>加一岁</button> 
        <button v-on:click='age--'>减一岁</button> 
VUE将函数绑定到事件  
HTML部分
<button v-on:click='add'>加一岁</button> 
<button v-on:click='js'>减一岁</button> 

  
js部分
var nn = new Vue({
    el:'#lx',
    data:{
        name:'小阳阳',
        age:'18',
        sex:'小女僧',
        link:'www.baidu.com',
        tag:'<a href="www.baidu.com">百度</a>' 
    },
    methods:{
        aa:function(){
            return this.name+this.age+this.sex 
        },
        add:function(){
            return this.age++;
        },
        js:function(){
            return this.age--;
        }
    }
});
 如果想加十岁或减十岁可以用传参的形式
HTML部分
<button v-on:click='add(10)'>加一岁</button>  等价于<button @click='add(10)'>加一岁</button> 
<button v-on:click='js(10)'>减一岁</button> 

  
js部分
var nn = new Vue({
    el:'#lx',
    data:{
        name:'小阳阳',
        age:'18',
        sex:'小女僧',
        link:'www.baidu.com',
        tag:'<a href="www.baidu.com">百度</a>' 
    },
    methods:{
        aa:function(){
            return this.name+this.age+this.sex 
        },
        add:function(a){
            return this.age+=a;
        },
        js:function(){
            return this.age-=a;
        }
    }
});
								        进度:99%



