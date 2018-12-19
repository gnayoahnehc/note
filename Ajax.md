##Ajax

```
什么是ajax？
	async javascript and xml  异步的js和xml的应用
	
	创建了交互式的网页开发技术

什么地方见过ajax?
	百度图片  小说无刷新应用。。地图加载缩放

ajax的作用？
	无刷新的数据交互  用于提高用户体验

学习ajax需要哪些知识？ 
	js  html  css  dom   php..

ajax的构造原理 
	http 请求机制分类：
		同步请求：
			一个进程在执行的过程中，没有返回结果信息之前会一直等待，下面的程序不会执行，
			直到结果信息返回之后才会执行
		异步请求：
			进程在执行的过程中不需要等待结果信息，下面的程序会继续执行，有信息返回就处理。

ajax：是js中的一个对象

var 变量=new XMLHttpRequest();

一般来说ajax都是存在于事件当中
```



###成员属性

```
onreadystatechange:判断请求与相应状态事件
	readyState：发送请求的状态 0-4
		0： 未初始化 还没有调用send方法
		1：载入 调用send方法正在发送
		2：载入完成 send发送完成 以接收响应
		3：交互 解析收到的响应内容
		4：响应的内容解析完成 可以在浏览器显示

	status：响应信息状态码
		200  成功
		404  报错  错误
		not  found  没有找到

	responseText：响应信息的主体内容为文本格式
		浏览器接收服务器返回的结果信息
```



### 成员方法

```
open(): 建立请求
	参数1：发送数据的方式 get post
	参数2：请求发送的文件地址
	参数3：是否异步请求 默认值 true异步 false 同步

send(): 发送请求
	注意：没有参数直接省略或者是null 有参数发送参数

setRequestHeader():设置请求的头部信息
	值：请求的属性名 属性值 固定写法

localhost:本地服务器

```



###Ajax完整过程

```
// 创建ajax对象
var xml=new XMLHttpRequest();
	
//1.建立请求 请求方式 文件地址 是否异步
xml.open('post','php/2.php',true);

// 设置请求的头部信息
xml.setRequestHeader('Content-type','application/x-www-form-urlencoded');

//2.发送请求 post 发送数据
xml.send('username=史珍香'); 

//3.判断监听事件 发送 响应
xml.onreadystatechange=function(){
	// 发送请求 0-4状态
	console.log(xml.readyState);

	// 响应成功 200
	console.log(xml.status);

	// 判断 请求成功  返回信息成功
	if(xml.readyState==4 && xml.status==200){
		// 获取服务器返回的信息
		document.write(xml.responseText);
	}
}
```