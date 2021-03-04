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
4. absolute 相对于最近的以定位(非static)的父元素
5. sticky 粘性定位，适用于导航栏，元素表现为，根据正常文档流进行定位，然后相对它的最近滚动祖先定位
- 重叠的元素：position 不为static，根据z-index 来显示谁上谁下；

## rem em vw vh px
- rem:相对于根元素的字体大小
- em：相对于父元素的字体大小
- vw：基于视口宽度的大小，100vw相当于全宽
- vh：基于视口高度的大小，100vh相当于全高
- px：基于显示器分辨率的大小

## margin,padding值为%的时候
- 是依据父元素的width来计算的；

## 解析css规则树
- 从右往左解析
- why？ 因为这样是从树的下面往上遍历，节省了大量错误匹配的时间，能大大优化解析速度；

## float
- float元素半脱离文档流，其他盒子会无视这个元素，但其他盒子内的文本依然会为这个元素让出位置，环绕在周围；
- absolute是完全脱离文档，

## 重排重绘优化
- 核心策略是减少dom操作，要一次性操作，避免反复操作
1. 先将元素脱离文档流，在对其进行修改
2. 使用fragment文档片段，
3. 动画元素脱离文档流，这样避免其他元素的重排重绘，只影响自身，降低重排重绘损耗；
4. 硬件加速方式，使用transform，3D动画等方式开启一个新的复合图层，不会影响默认的复合图层（普通文档流），这样不会影响周边的DOM结构，而属性的改变也会交给GPU处理，不会发生重排重绘；

## transform对元素的影响
- 会新开一个复合图层，fixed定位也是依据复合图层定位的，详情见上。

## 可继承的属性
- font： font-size,font-weight,font-family
- text: text-align,text-transform,text-indent
- color
- line-height,visibility,cursor
- list: list-style-type,list-style,list-style-image

## transition使用
- 在状态切换时产生过度效果，比如渐隐渐显
```CSS
.div {
  transition: opacity 2s 0.5s // 作用属性透明度，过渡持续时间2s ,延迟过度0.5s;
}
```