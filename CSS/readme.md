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
