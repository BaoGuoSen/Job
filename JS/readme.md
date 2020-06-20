## 函数声明和函S数表达式的区别
  JS有变量声明提升机制，函数声明会存在变量提升，即无论将函数声明写在哪里，js会把它放在最前面。<br>
  函数表达式只有在js运行到这个地方的时候才会变得有效<br>
  函数声明在js解析时提升，函数表达式在js运行并表达式运行完后才能进行调用<br>
  例：
  
 ```JavaScript
getName()//oaoafly
var getName = function() {
	console.log('wscat')
}
getName()//wscat
function getName() {
	console.log('oaoafly')
}
getName()//wscat
```
## Ajax（Asynchronous JavaScript And XML）
#### XMLHttpRequest 对象属性
##### readyState: 保存XMLHttpRequest的状态
- 0:未初始化。未调用open（）
- 1：启动。已经调用open（）方法，未调用send（）
- 2：发送。调用send（），未接收到数据。
- 3：接收。收到部分数据。
- 4：完成。收到全部数据，且可以使用。
##### status：返回请求的状态码
- 200：“OK”
- 403：“Forbidden”
- 404：“Not Found”
```JavaScript
var xhr = new XMLHttpRequest();
xhr.onreadystatechange = function () {
	if(xhr.readystate ==4 && xhr.status = 200)
		console.log(xhr.responseText);
	else
		console.error(xhr.status);
xhr.open("get","url",true);//true为异步请求，false为同步请求
xhr.send();
```
