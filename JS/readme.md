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

## 延迟加载js脚本的方法
- async js加载完成后立即执行；
- defer 加载与加载文档并行执行，但是在文档完成加载后js脚本才执行；

## 闭包的作用及缺陷
1. 作用：
- 柯里化
- 防抖节流
- 私有变量
2. 缺陷:
- 使用过多会有内存泄漏的问题（所引用的变量一直得不到释放）

## Object 与 Map的区别
1. Object只能把String和Symbol作为key值，而Map的key值的类型没有限制；
2. map有size能很方便获取map长度，而Object没有直接获得长度的方法；
3. map实现了迭代器，能使用for of遍历，而Object没有；不能使用for of 遍历；

## 判断函数是被new还是被调用
1. ES6
- es6函数有个new.target元属性，被new调用时，指向构造函数本身，函数调用指向undefined
```JavaScript
function fn() {
  if (new.target) {
    console.log('new')
  }
}
```
2. es5
- 函数内部this.constructor,被new调用指向构造函数本身，函数调用指向window
```JavaScript
function fn() {
  if (this.constructor === fn) {
    console.log('new')
  }
}
```

## Object.prototype.toString.call()原理
1. 对于undefined返回[object,undefined]
2. 对于null返回[object,null]
3. 将this转为Object
4. 访问内部属性[class]的值
5. 返回[object,class]

## 事件为什么通常在冒泡阶段执行
- 由子到父，意味着是由精确到模糊，可以更准确的进行事件处理
- 同时在这个阶段还能阻止事件的冒泡传递；

## 递归爆栈解决办法
- 尾调优化
```JavaScript
function fib(n,pre,next) {
  if (n === 0) {
    return pre
  } else {
    return fin(n-1,next,pre+next)
  }
}
```
- 问题：尾调优化是个隐式行为，如果代码存在死循环，原本会爆栈变得无法爆栈报错，而无法被发现
- 优化后，调用栈信息丢失，调试困难

