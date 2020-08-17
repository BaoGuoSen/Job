## 容器的属性
1. flex-direction：定义主轴的排列方向
```CSS
.box {
  flex-direction: row | row-reverse | column | column-reverse;
}
```
2. flex-wrap:一条轴线装不下，换行的策略；；
```CSS
.box{
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```
3. justify-content:定义项目在主轴上的对齐方式
```CSS
.box {
  justify-content: flex-start | flex-end | center | space-between | space-around;
}
```
4. align-items:定义项目在交叉轴上的对齐方式
```CSS
.box {
  align-items: flex-start | flex-end | center | baseline | stretch;
}
```
5. align-content:定义了多根轴线的对齐方式，如果项目只有一根轴线，该属性不起作用
```CSS
.box {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}
```
## 项目的属性
1. order：定义项目的排列顺序，数值越小，排列越靠前，默认为0；
```CSS
.item {
  order: <integer>;
}
```
2. flex-grow：定义项目的放大比例
3. flex-shrink：定义项目的缩写比例
4. flex-basis：定义了在分配多余空间之前，项目占据的主轴空间；
5. flex：是flex-grow，flex-shrink，flex-basis的缩写，flex：1为flex：1 1 0；
6. align-self：默认继承父元素align-items属性，允许单个项目与其他项目不一样的对齐方式；
