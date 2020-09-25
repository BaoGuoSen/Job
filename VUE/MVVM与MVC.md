#### 参考链接：https://zhuanlan.zhihu.com/p/87752772

## MVC
- View：对应于布局文件（视图）
- Model：业务逻辑和实体模型（数据）
- Controller：对应于Activity；
- 数据单向的

## MVVM
- 将MVC的C变为了ViewModel；
- 实现了数据的双向绑定；
- 优点：
1. 低耦合:View可以独立于Model变化和修改,一个ViewModel可以绑定到不同的View上,当View变化的时候Model可以不变,当Model变化的时候View也可以不变。
2. 可重用性: 可以把一些视图逻辑放在一个ViewModel里面,让很多View重用这段视图逻辑。
3. 独立开发: 开发人员可以专注于业务逻辑和数据的开发,设计人员可以专注于页面的设计。

## MVVM和MVC的区别
- MVC中Controller演变成MVVM中的ViewModel
- MVVM通过数据来显示视图层而不是节点操作
- MVVM主要解决了MVC中大量的dom操作使页面渲染性能降低,加载速度变慢,影响用户体验
