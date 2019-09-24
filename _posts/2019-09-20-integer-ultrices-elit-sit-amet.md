---
title: 2019年9月20日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---
## sass
    
            sass启动：
1.在文件夹中创建一个html文件和一个scss文件
2.在本文件夹下使用小黑框输入sass --watch scss文件名:要生成的css文件
3.这个时候scss文件中写样式，css会同步更新，
4.用html链接css文件，向scss文件中写样式css也会同步更新，这样html也就会接收到样式
定义变量：
$变量名:值；
嵌套css样式
html部分：
 <div class='d1'>
        <ul class='u1'>
            <li class='l1'>齐健</li>
            <li class='l2'>小灰灰</li>
            <li class='l3'>
                <span>小阳阳</span>
            </li>
        </ul>
    </div>
css部分：

.d1{

    .u1{
        .l1,.l2,.l3{
            span{
                color:green;
            }
            list-style: none;
        }
        width:200px;
        height:200p;
        background:pink;
    }
    width:300px;
    height:300px;
    background:red;
}
css的选择器中可以写伪元素选择器
.d1{
    width:300px;
    height:300px;
    background:red;
    .l1:hover{
        background:pink;
    }
}
给元素添加默认样式 含义是：如果这个变量被声明赋值了，那就用它声明的值，否则就用这个默认值。
$fancybox-width: 400px !default;
.fancybox {
width: $fancybox-width;
}
变量的定义：sass允许使用变量，所有的变量以$开头，如果变量需要镶嵌在字符串中，就必须用#{}使用
如：width:#{$变量名}px
$num:5;
.border{
width:$num*2px;
fontsize:$num+px;
height:#($num * $num)这样是可以的
height:#{$num}+#{$num}； ！！！这样不可以，会被认为是变量的值拼接
}
复用功能(继承)：
继承例子：
@extend用法：
.center{
    text-align: center;
}
li{
    width:100px;
    height:50px;
    background:red;
    @extend .center;
}
@mixin的用法
@mixin center($f){
    text-align:$f;
}
li{
    width:100px;
    height:50px;
    background:red;
    @include center(center);
}
导入文件
可以插入两种文件一种是css文件一种是编译后的scss文件
导入scss文件(不用打后缀名)：
@import 'a';
导入css文件(后缀名不能省略):
@import ‘b.css’;
if语句：
@mixin wid($b){
    @if($b==5){
        background:red;
    }@else if($b>5){
        background:green;
    }
}
body{
    @include wid(6)
}
for循环语句：
@for $i from 1 to 10{
 类名#{$i}{
    background-image:url('#{$i}.jpg')
}
}
echo语句：
@each $k in 1,2,3,4,5{
    类名#{$k}{
        background-image:url('#{$k}.jpg')
    }
}
function函数：
@function color($r,$g,$b,$a){
    @return rgba($r,$g,$b,$a);
}
body{
    background:color(1,1,1,0.5);
}
