## 水平垂直居中
1. 使用flex布局
```CSS
.wrapper {
  display: flex;
}
.center {
  margin: auto;
}
```
2. flex布局，父元素指定子元素居中
```CSS
.wrapper {
  display:flex;
  justify-content:center;
  align-items:center;
}
```
3. 绝对定位，将中心点平移自身宽高一半
```CSS
.center {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```
## CSS样式优先级
- ！important > 内联样式 > ID 选择器 > 类选择器 = 属性选择器 = 伪类选择器 > 标签选择器 = 伪元素选择器
## 为什么img是行内元素还可以设置宽高
- 首先引入替换元素（空元素，没有实际的内容），不可替换元素（有实际内容，<p>）
- 替换元素有内在的宽高。（不设置就默认为实际的宽高）
  
## CSS画图
- https://css-tricks.com/the-shapes-of-css/
  
## 内联元素和块级元素
- 内联元素特点
1. 和其他元素都在一行上；
2. 元素的高度、宽度及顶部和底部边距不可设置；
3. 元素的宽度就是它包含的文字或图片的宽度，不可改变。
- 块级元素特点
1. 每个块级元素都从新的一行开始，并且其后的元素也另起一行。（真霸道，一个块级元素独占一行）
2. 元素的高度、宽度、行高以及顶和底边距都可设置。
3. 元素宽度在不设置的情况下，是它本身父容器的100%（和父元素的宽度一致），除非设定一个宽度。
  
## 伪类和伪元素
1. 伪类的效果可以通过添加一个实际的类来达到，而伪元素需要通过一个实际的元素来达到；
2. css3中单冒号：表示伪类，双冒号：：表示伪标签；
3. 常见伪类；：link，：vistied，：hover，：focus；
4. 常见伪元素；：：before，：：after；
  
## 为什么要清除浮动
1. 当子元素发生浮动并且高度大于父元素，父元素会发生高度塌陷；

## 清除浮动的方法
1. 在最后一个子元素的后面添加一个块级元素，将其设置clear：both；
2. 和方法一类似，使用伪元素清除浮动
3. 将父元素设置为bfc（overflow：auto）；

## BFC
1. 块级格式化上下文，有独立的渲染规则，不受外部影响，也不影响外部；
2. 触发bfc：
- body根元素
- 浮动元素：float除none以外的值；
- 绝对定位元素：absolute，fixed；
- display为inline-block，flex；
- overflow除了visible以外的值
3. 作用
- 避免外边距的重叠
- 清除浮动
- 避免文字环绕

## css导入link与@import的区别
1. link
- 是XHTML标签，除了加载css外还可以定义其他事务；
- 在页面载入时同时加载；无兼容问题；
2. @import
- 只能加载css文件
- 需要页面完全加载后才能加载；

## 设置节点样式方法
1. 直接设置style属性：node.style.height = "100px";
2. 直接设置class属性：node.setAttribute("class","test");(test为style中的class);

## position定位
1. static 默认值，遵循正常的文档流；
2. fixed 相对于浏览器窗口的位置；
3. relative 相对其正常的位置，依然占据原本的空间
4. absolute 相对于最近的以定位的父元素
5. sticky 根据用户的滚动位置来定位；
- 重叠的元素：脱离文档流的元素发生重叠，根据z-index 来显示谁上谁下；
