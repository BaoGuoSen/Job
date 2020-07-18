## vue双向绑定原理及响应原理
1. 利用Object.propertyjie创建一个观察者劫持监听所有的属性
2. 将这些属性转化为getter和setter
3. 每个组件都有watcher实例并且将所有属性通过getter收集为依赖
4. 当依赖项触发setter时，会通知watcher并更新渲染相应的组件
![Alt text](https://github.com/BaoGuoSen/Job/blob/master/imgs/%E5%8F%8C%E5%90%91%E7%BB%91%E5%AE%9A.png)
