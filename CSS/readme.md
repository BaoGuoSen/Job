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
## CSS样式优先级
- ！important > 内联样式 > ID 选择器 > 类选择器 = 属性选择器 = 伪类选择器 > 标签选择器 = 伪元素选择器
## 为什么img是行内元素还可以设置宽高
- 首先引入替换元素（空元素，没有实际的内容），不可替换元素（有实际内容，<p>）
- 替换元素有内在的宽高。（不设置就默认为实际的宽高）
