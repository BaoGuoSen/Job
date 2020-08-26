#### this的指向在函数定义的时候是确定不了的，只有函数执行的时候才能确定this到底指向谁，实际上this的最终指向的是那个调用它的对象；
## this的几种指向
1. 作为函数调用，非严格模式下，this指向window，严格模式下，this指向undefined
2. 作为某对象的方法调用，this通常指向调用的对象；
3. 使用apply，call，bind可以绑定this的指向；
4. 在构造函数中，this指向新创建的对象；
5. 箭头函数没有this，this指向它的上一级；
6. 事件中的this指向e.currentTarget;
