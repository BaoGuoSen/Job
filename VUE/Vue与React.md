## 相同点
1. 都用了virtual dom ；
2. 都是基于js的框架

## 不同点
1. 模板语法
- Vue用模板语法
- React用jsx语法
2. 数据流
- Vue强调数据的双向性，所以是双向绑定的
- React强调数据的单向性，
3. 监听数据
- Vue通过getter/setter实现数据的劫持，能精确知道数据的变化
- React默认通过比较引用（diff）的方式进行的