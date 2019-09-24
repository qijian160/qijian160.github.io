---
title: 2019年9月21日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---
## bootstrap
 垂直对齐为align-items-center    参数为 center(中) end(下)
.            <div class='row align-items-center'>
                <div class=' col-2 col-sm-5 col-lg-2' style='background:red;'>1</div>
                <div class='col-5 col-sm-2 col-lg-2' style='background:green;'>1</div>
                <div class='col-5 col-sm-5 col-lg-5' style='background:yellow;'>1</div>
                <div class='col-5 col-sm-5 col-lg-3' style='background:yellowgreen;'>1</div>
            </div>
水平对齐为justify-content-end-end   参数为center(居中) end(右对齐)between(分散对齐) around(为平均分的对齐)


删除间距(gutters)：
no-gutters
    <div class='container' style='height:100px;background:pink;'>
            <div class='row align-items-center no-gutters'>
                <div class=' order-4' style='background:red;'>1</div>
                <div class=' order-1' style='background:green;'>2</div>
                <div class='' style='background:yellow;'>3</div>
                <div class='' style='background:yellowgreen;'>4</div>
            </div>
   </div>


排序(order-1到12)不被排序的在前然后是从1开始排  数越小越靠前
    <div class='container' style='height:100px;background:pink;'>
            <div class='row align-items-center no-gutters'>
                <div class=' order-4' style='background:red;'>1</div>
                <div class=' order-1' style='background:green;'>2</div>
                <div class='' style='background:yellow;'>3</div>
                <div class='' style='background:yellowgreen;'>4</div>
            </div>
   </div>


偏移：就是当列中不满12个格子，可以用偏移对列的位置进行调整 
偏移就是想在哪个div前偏移就往哪个div的class中添加offset
    <div class='container' style='height:100px;background:pink;'>
            <div class='row align-items-center no-gutters'>
                <div class=' order-4 offset-md-11' style='background:red;'>1</div>
                <div class=' order-1' style='background:green;'>2</div>
            </div>
   </div>


尺寸单位rem： 
就是成为px的多少倍，响应式布局的时候当到大页面尺寸的时候就将其改动rem的倍数
bootstrap的标签：
<small class='text-mutd'>内容</small>
此class类可以将其副标题颜色做出改变
强调显示class类可以用lead
图片的类：
将图片变成响应式，页面尺寸缩小的时候图片也变可以为img标签添加img-thumbnail的class类
将图片圆角rounded类
改变页面尺寸更换图片实例：
显示1.png图片的页面宽度最小是1000px;
显示2.png图片的页面宽度最小是800px;
显示3.jpg是在不满足任何情况的时候显示
<picture>
        <source srcset="1.png" media="(min-width:1000px)">
        <source srcset="2.png" media="(min-width:800px)">
        <img src="3.jpg" alt="">
    </picture>

    
