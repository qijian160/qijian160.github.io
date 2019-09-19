---
title: 2019年9月18日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---

#### VUE训练
  ```

对数组进行遍历： 这里的template标签就是容器渲染，如果用div将遍历出多个div如果使用template就不会了
     H5部分
  
          <ul> 
                <li  v-for="sz in szs"> 
                       {{sz}} 
                </li> 
                <li v-for='(user,index) in users'> 
                   {{index+1}}:{{user.name}}-{{user.age}} 
                </li> 
            </ul> 
            <template v-for='(user,index) in users'> 
                {{index+1}}:{{user.name}}-{{user.age}} 
            </template> 
    VUE部分 
 
       szs:['小阳阳','小阳人'], 
       users:[ 
           {name:'aa',age:18}, 
           {name:'bb',age:11} 
       ], 

  
接上一个代码  对数据的键名和值进行遍历
  <template v-for='(user,index) in users'> 
                <div v-for='(val,key) in user'> 
                    {{key}}-{{val}} 
                </div> 
            </template> 
实例化多个Vue，并使用bb改变aa中的name
html部分
  
<!DOCTYPE html> 
<html lang="en"> 
        <head 
        > 
                <meta charset="UTF-8"> 
                <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
                <meta http-equiv="X-UA-Compatible" content="ie=edge"> 
                <title>Document</title> 
                <script src="https://cdn.staticfile.org/vue/2.4.2/vue.min.js"></script> 
            <link rel="stylesheet" href="css.css"> 
            </head> 
             
<body> 
    <div id='aa'> 
        <p>{{name}}</p> 
    </div> 
    <div id='bb'> 
        <p>{{name}}</p> 
        <button @click='chang'>change</button> 
    </div> 
    <script src="lx2.js"></script> 
</body> 
</html> 
 

 
vue部分
 
var aa = new Vue({ 
    el:'#aa', 
    data:{ 
        name:'aa', 
    } 
}) 
var bb = new Vue({ 
    el:'#bb', 
    data:{ 
        name:'bb', 
    }, 
    methods:{ 
        chang:function(){ 
            aa.name='cc'; 
        }, 
    } 
}) 

  
初识组件的应用
Vue部分
  
 
Vue.component('aa',{ 
    template:"<p>  {{name}}   小阳阳</p>", 
    data:function(){ 
        return{ 
            name:'zz', 
        } 
    } 
}) 
new Vue({ 
    el:'#aa', 

 
}) 
new Vue({ 
    el:'#bb', 

 
}) 
 
 

  
h5部分 
 
<!DOCTYPE html> 
<html lang="en"> 
        <head > 
                <meta charset="UTF-8"> 
                <meta name="viewport" content="width=device-width, initial-scale=1.0"> 
                <meta http-equiv="X-UA-Compatible" content="ie=edge"> 
                <title>Document</title> 
                <script src="https://cdn.staticfile.org/vue/2.4.2/vue.min.js"></script> 
            <link rel="stylesheet" href="css.css"> 
            </head> 
<body> 
    <div id='aa'> 
        <aa></aa> 
    </div> 
    <div id='bb'> 
    <aa></aa> 
    </div> 
    <script src="lx2.js"></script> 
</body> 
</html> 
 
在APP.vue中使用import后必须要用components:进行注册一下组件


```
								        进度:60%



