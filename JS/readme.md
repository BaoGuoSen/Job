## 函数声明和函数表达式的区别
  
    js有变量声明提升机制，函数声明会存在变量提升，即无论将函数声明写在哪里，js会把它放在最前面。<br>
  函数表达式只有在js运行到这个地方的时候才会变得有效<br>
  函数声明在js解析时提升，函数表达式在js运行并表达式运行完后才能进行调用<br>
  例：
  
    	getName()//oaoafly
		var getName = function() {
			console.log('wscat')
		}
		getName()//wscat
		function getName() {
			console.log('oaoafly')
		}
		getName()//wscat
