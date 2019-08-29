---
title: 2019年8月29日 日报 
teaser: 让努力成为一种习惯
tags: [markdown, workflow, foss]
---

#### javascript
##### 计时器：
  ```
  <!DOCTYPE html>
<html>
	<head>
		<title></title>
	
	</head>
	<body>
		<button id='aa'onclick='btnclicked()'>按钮</button>
		<p id='ptime'></p>
		<script type="text/javascript">
			var time=setInterval(function(){
				gettime();

			},1000);
			function gettime(){
				var d=new Date();
				var t=d.toLocaleTimeString();
				document.getElementById("ptime").innerHTML=t;
			};
		function	btnclicked(){
			clearInterval(time);
		}
		function out(){
			var vv=setTimeout(function(){
				alert('hello');
			},3000);
		}
		</script>
		<button id='out'onclick='out()'>3秒</button>
	</body>
</html>		
  ```
								        进度:100%
#####轮播图
  ```
<!DOCTYPE html>
<html>
<head>
	<title></title>
	<style type="text/css">
		*{
			margin:0px;
			padding: 0px;
		}
		#div{
			width:540px;
			height:400px;
			margin:50px auto;
			background: green;
			padding:5px 0px;
			position: relative;
			overflow: hidden;
		}
		#ul{
			/*width:530px;*/
			height:130px;
			position:absolute;
			/*left:-136px;*/
		}
		#div li{
			list-style: none;
			float:left;
			margin:5px;	
				
		}
		#an{
			position: absolute;
		}
		#an a{
			float: left;
			width: 10px;
			height:20px;
			background: pink;
			margin: 0px 5px;
		}
		#an a:hover{
			background-color: black;
		}
	</style>

</head>
<body>
	<div id='div'>
		<ul id='ul'>
			<li name='li1'>
				<img src="q.jpg">
			</li>
			<li name='li1'>
				<img src="w.jpg">
			</li>
			<li name='li1'>
				<img src="e.jpg">
			</li>
			<li name='li1'>
				<img src="r.jpg">
			</li>
		
		</ul>
		<div id="an">
			<a href="javascript:;">1</a>
			<a href="javascript:;">2</a>
			<a href="javascript:;">3</a>
			<a href="javascript:;">4</a>
		</div>
	</div>

	<script type="text/javascript">
		var img = document.getElementById("ul");
		var imgarr=document.getElementsByTagName("img");
		img.style.width=1300*imgarr.length+"px";
		var an = document.getElementById("an");
		var anfu=document.getElementById("div");
		an.style.left=(anfu.offsetWidth - an.offsetWidth)/2+"px";
		var all=document.getElementsByTagName("a");
		var index = 0 ;
		all[index].style.backgroundColor='black';
		for(var i=0;i<all.length;i++){
				all[i].num = i;
			all[i].onclick=function(){
				index=this.num;
				img.style.left=-530*index+"px";
			}

		}	
  ```
								        进度:100%