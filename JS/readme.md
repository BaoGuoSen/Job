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
## 箭头函数与普通函数的区别
- 没有this
- 没有arguments
- 没有super
- 无法作为构造函数（没有原型对象）
## JS垃圾回收机制
1. 标记清除（常见）
- 垃圾收集器在运行的时候回给存储在内存中的所有变量加上标记，然后会去掉环境中的变量以及被环境中的变量所引用的变量的标记，在此之后会清除仍然还存在标记的变量。
2. 引用计数（不常见）
- 跟踪记录每个值被引用的次数，如果次数为0就清除，可是存在一个循环引用的问题，使得引用次数永远不可能为0就永远不会被清除。
## JS创建对象的方式
1. 工厂模式
```JavaScript
function Person() {
  var o = new Object();
  o.name = 'hanmeimei';
  o.say = function() {
    alert(this.name);
  }
  return o;
}
var person1 = Person();
```
- 优点：解决了创建多个相似对象的问题
- 缺点：无法识别对象的类型，全是Object
2. 构造函数模式
```JavaScript
function Person() {
  this.name = 'hanmeimei';
  this.say = function() {
    alert(this.name)
  }
}
var person1 = new Person();
```
- 优点：可以通过instanceof识别对象的类型
- 缺点：每个实例的方法都是一样的，浪费资源。
3. 原型模式
```JavaScript
function Person() {}
Person.prototype.name = 'hanmeimei';
Person.prototype.say = function() {
  alert(this.name);
}
var person1 = new Person();
```
- 优点：方法共享了
- 缺点：由于所有实例共享原型对象的对象，如果有数组，实例对其更改，那么所有实例的数组对象都被更改了
4. 构造函数和原型模式的组合（最常见）
```JavaScirpt
function Person(name) {
  this.name = name
  this.friends = ['lilei']
}
Person.prototype.say = function() {
  console.log(this.name)
}
var person1 = new Person('hanmeimei')
person1.say() //hanmeimei
```
- 优点：解决了共享方法的缺点
5. 动态原型模式
``` JavaScript
function Person(name) {
  this.name = name
  if(typeof this.say != 'function') {
    Person.prototype.say = function(
    alert(this.name)
  }
}
```
- 优点：将原型对象封装在构造函数里，变得更直观
## JS和Css动画的区别
1. js是单线程可能会造成阻塞
2. js动画的效果更好，也能更好的控制
3. css动画的控制很弱，只能暂停，无进度报告等
4. css动画使用requestAnimationFrame会比js流程
5. requestAnimationFrame不卡顿原理，将每一帧中的Dom操作集中起来，在一次重排和重绘中完成，并且重排或重绘的时间间隔紧紧跟随浏览器的刷新频率（每秒60帧）

## 内存泄漏与内存溢出
- 内存泄漏是指程序在申请内存后，无法释放已申请的内存空间；
- 内存溢出是指程序在申请内存时，没有足够的内存空间供其使用；
- 内存泄漏大量累积会造成内存溢出；
