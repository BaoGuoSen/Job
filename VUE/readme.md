## vue双向绑定原理及响应原理
1. 利用Object.propertyjie创建一个观察者劫持监听所有的属性
2. 将这些属性转化为getter和setter
3. 每个组件都有watcher实例并且将所有属性通过getter收集为依赖
4. 当依赖项触发setter时，会通知watcher并更新渲染相应的组件
![Alt text](https://github.com/BaoGuoSen/Job/blob/master/imgs/%E5%8F%8C%E5%90%91%E7%BB%91%E5%AE%9A.png)
## v-if 和 v-show的区别
1. 相同点：两者都是判断DOM节点是否显示
2. 不同点：v-if会在切换过程中对条件块的事件监听器和组件进行销毁和重建初始是false什么也不干
3. v-show只是基于css进行切换，不管什么条件都会渲染
4. 适用：v-if切换性能消耗大，适合初始化渲染。v-show初始化渲染性能消耗大，适合频繁切换渲染
## vue3.0采用Proxy监听数据而舍弃了defineProperty呢？
1. defineproperty不能监测数组下标的变化（实际项目中也遇到了这个问题，更新数组下标的某一值，页面无更新）；
2. Object.defineProperty只能劫持对象的属性，而Proxy是直接代理对象；
3. Proxy支持13种拦截操作，这是defineProperty所不具有的；
4. Object.defineProperty对新增属性需要手动进行Observe；
5. proxy兼容性很差，对ie浏览器来说就是灾难。
## vue中key的作用
1. 高效的更新虚拟DOM
2. 在同级的 vnode diff 过程中，可以根据 key 快速的对比，来判断是否为相同节点，并且利用 key 的唯一性可以生成 map 来更快的获取相应的节点。
## 父子组件通信
1. props向下传递，事件冒泡向上传递；
2. v-model实现双向绑定；
## 页面组件间的传值
1. 使用vue-router跳转链接带参数；
2. 使用本地缓存localstorage；
3. 使用vuex数据管理传参。
## keep-alive组件的作用
1. keep-alive 可以在组件切换时，保存其包裹的组件的状态，使其不被销毁，防止多次渲染。
其拥有两个独立的生命周期钩子函数 actived 和 deactived，使用 keep-alive 包裹的组件在切换时不会被销毁，而是缓存到内存中并执行 deactived 钩子函数，命中缓存渲染后会执行 actived 钩子函数。
