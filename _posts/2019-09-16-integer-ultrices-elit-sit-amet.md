---
title: 2019年9月16日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---

#### JQ训练
  ```
html连接jq必须加一行这个代码：
  
 <script src="https://cdn.staticfile.org/jquery/1.10.2/jquery.min.js"></script>   
  
陌生： 
  
 parents('元素名')  
  
    上一级的什么元素
  
  $("#div1").fadeIn();  
  
    渐变，淡入
  
  $("#div1").fadeToggle();  
  
    渐变 淡入,淡出
  
  $("#div2").fadeTo("slow",0.4);  
  
    设置透明
  
  $('#div').slideUp("slow");  
  
  
  $('#div').slideDown("slow");  
  
  设置滑动消失
  
  $("#div1").fadeToggle();  
  
  设置显示消失

 
jq选择器基础选择器:
    #id:根据给定的id匹配一个元素fadein
    .classname:根据给定的类名匹配一个元素
   attr('class'):根于给定的元素名匹配元素
 
    *:匹配所有元素
    select1,select2:将每一个匹配到的元素合并后一起返回

jQuery选择器大致概括

1.父级：

jQuery.parent(expr) 找父亲节点，可以传入expr进行过滤，比如$("span").parent()或者$("span").parent(".class")

jQuery.parents(expr),类似于jQuery.parents(expr),但是是查找所有祖先元素，不限于父元素

2.子级：

jQuery.children(expr).返回所有子节点，这个方法只会返回直接的孩子节点，不会返回所有的子孙节点

jQuery.contents(),返回下面的    所有内容，包括节点和文本。这个方法和children()的区别就在于，包括空白文本，也会被作为一个jQuery对象返回，children() 则只会返回节点

3.同级：

jQuery.prev()，返回上一个兄弟节点，不是所有的兄弟节点

jQuery.prevAll()，返回所有之前的兄弟节点

jQuery.next(), 返回下一个兄弟节点，不是所有的兄弟节点

jQuery.nextAll()，返回所有之后的兄弟节点

jQuery.siblings(), 返回兄弟姐妹节点，不分前后

4.全部

jQuery.find(expr), 跟jQuery.filter(expr)完全不一样。jQuery.filter()是从初始的jQuery对象集合中筛选出一部分，而jQuery.find() 的返回结果，不会有初始集合中的内容，比如$("p"),find("span"),是从p元素开始找,等同于$("p span")

jq层次选择器:
    ancestor descendant:选取ancestor元素里的所有descendant元素(无论是孙子级别还是儿子级别都会被匹配)
    paren>child:获取parent元素下的child元素(只去匹配儿子级别的元素)
    prev+next:选取紧接在prev元素后的next元素(找出prev下的第一个next元素)
    prev~next:选取紧接在prev元素后的所有next元素
jq常用的基本过滤选择器
    :first:选取第一个元素
    :last:选取最后的元素
    :not(selector):去除所有与给定选择其匹配的元素
        例:$(input:not(.myclass))剔除class名为myclass的input元素
    :even:选取索引值为偶数的所有元素，从0开始
    :odd:选取奇数的元素
    :eq(index):匹配一个给定索引值元素,从0开始
        例:$("div:eq(1)")
    :gt(index):匹配大于索引值的元素，从0开始
        例:$("div:gt(1)");
    :header:选择h1,h2,h3一类的标签
    :animated:匹配正执行动画效果的元素
    :current：下的第一个元素 
 
jq常用的基本过滤选择器
    :contains(text):匹配包含给定文本的元素
        $("标签:contains('查找的文本')");
    :empty:匹配所有不包含子元素或者文本的空元素(查找空元素)
    :has(selector):匹配含有选择器所匹配元素的元素
    :parent:选取含有子元素或者文本的元素
jq常用的可见性过滤选择器
    :hidden:选取所有不可见的元素
    :visible:选取所有可见的元素
jq事件
    在jq中使用的是$(document).read()方法——$()方法
    在jq中使用的是window.onload方法
    区别：
        执行时机不同：
            window.onload方法是在网页中的元素(包括元素的所有关联文件)完全加载到浏览器后执行，即javascript此时才可以访问网页中的任何元素
            $(document).ready()方法在DOM完全就绪时就可以被调用，无需等待元素的相关联文件下载完毕，可以大大提高程序的响应速度。 
        使用次数不同：
            window.onload事件一次只能保存一个函数的引用
            $(document).ready()方法每次调用都会在现有的行为上追加新的行为
        执行的次数不同：
            window.onload只能绑定一个函数，只是最后绑定的函数被引用
            $(document).ready()可以绑定多个函数，并且每个绑定的函数都会被引用
        可以两种方式结合使用:
            将window绑定在$(document).ready()上
            $(window).load(function(){});
            这样可以让$(document).ready()方式得出DOM树后再得到所有属性或元素后再输出
jq的事件绑定
    bind()方法对元素进行事件绑定
        语法：bind (type,[data],fn)
        简洁语法：.type(fn)
            type是事件类型，如点击事件等
            data主要是传递给处理函数，很少能用到
            fn出发了这个事件交给哪个函数来处理
        例:("div").bind("click",function(){}); 就是绑定一个事件
        例:("div").bind("mouseover mouseout",function(){});同时绑定多个事件
                      mouseover鼠标移入事件  mouseout鼠标移出事件
    jq常用的事件类型
        click单击事件  dbclick双击事件，blur失去交流事件,focus获得焦点事件 等等  看截图
   
    合成事件：
        hover(enter,leave)方法
            用于模拟光标悬停事件，当鼠标移动到元素上的时候会调用enter函数，当鼠标离开的时候会出发leave函数
        toggle(fn1,fn2,fn3)方法
            用于绑定两个或多个事件处理器函数，以响应被选元素的六论的click事件
            toggle()方法是点击第一次的时候显示第一个函数，点击第二次的时候显示第二个函数，轮流执行
            toggle()方法可以是无参的，也可以是有参的，无参的就是点击以下出现再点击以下就消失的效果

 
jq事件对象：
        语法：
            $("元素或变量").bind("事件",function(){})
防止事件冒泡：冒泡事件就是逐级向上级执行，多个匿名函数顺序执行也是冒泡，是用这种方法可以停止冒泡 

 
        使用：event.stopPropagation()方式来停止事件冒泡
阻止默认行为   例如使用表单中的submit提交按钮，并在script代码中书写一个函数并赋予单击指令，这个时候就会执行函数中的代码，并不会提交
        使用：event.preventDefault()方法来组织元素的默认行为  
同时对事件对象停止冒泡和默认行为
        使用：return false
常用的事件对象属性
        
  ```
								        进度:99%



