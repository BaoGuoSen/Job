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
## 页面组件间的传值
1. 使用vue-router跳转链接带参数；
2. 使用本地缓存localstorage；
3. 使用vuex数据管理传参。
## keep-alive组件的作用
1. keep-alive 可以在组件切换时，保存其包裹的组件的状态，使其不被销毁，防止多次渲染。
其拥有两个独立的生命周期钩子函数 actived 和 deactived，使用 keep-alive 包裹的组件在切换时不会被销毁，而是缓存到内存中并执行 deactived 钩子函数，命中缓存渲染后会执行 actived 钩子函数。
## vue路由hash和history
1. url 展示上，hash 模式有“#”，history 模式没有
2. 刷新页面时，hash 模式可以正常加载到 hash 值对应的页面，而 history 没有处理的话，会返回 404，一般需要后端将所有页面都配置重定向到首页路由。
3. 兼容性。hash 可以支持低版本浏览器和 IE。
- hash模式原理
1. #后面 hash 值的变化，不会导致浏览器向服务器发出请求，浏览器不发出请求，就不会刷新页面。同时通过监听 hashchange 事件可以知道 hash 发生了哪些变化，然后根据 hash 变化来实现更新页面部分内容的操作。
- history原理
1. history 模式的实现，主要是 HTML5 标准发布的两个 API，pushState 和 replaceState，这两个 API 可以在改变 url，但是不会发送请求。这样就可以监听 url 变化来实现更新页面部分内容的操作。
## 为什么vue不要用index作为key
1. 当对节点操作时，key和值不同步；key永远是按下标来的，而值进过操作后，与之前的key可能会不匹配；
## 为什么不用随机数作为key
1. 新树的节点的key都是新的，在旧树中永远找不到，就会造成不可复用，每次都要新建，增加性能开销；
## vue路由懒加载
- 在路由配置里使用import导入组件，而不是在头部导入所有需要的组件；
## computed和watch的区别
- computed是计算属性，根据依赖的数据动态显示新的计算结果，在getter执行后会缓存computed的值，如果依赖属性值改变，下一次会重新对应的getter计算computed的值；
- watch是一个data的数据监听回调；当数据改变时，会触发watch；
## Object.defineProperty和proxy的优劣区别
1. vue3.0使用proxy监听对象；
2. proxy可以直接监听数组的变化；
3. proxy有多达13种拦截方法；
4. 不需要像Object.defineProperty一样遍历对象属性，直接代理对象；
## v-model原理
- <input v-bind:value="msg" v-on:input="msg=$event.target.value" />
- v-model本质上是语法糖，使用v-bind绑定数据，v-on：监听数据；
## v-if不能和v-for一起使用的原因
1. 可以一起使用但应该尽量避免
2. v-for的优先级要比v-if高，当处于同一节点时，意味着v-if将分别重复运行于每个v-for循环中；所以应该尽量避免；
## vue组件间的通信
1. 父子之间的通信：props/$emit,$children/$parent;
2. 兄弟间通信，全局通信：eventBus/Vuex；
3. 参考链接：https://juejin.im/post/6844903887162310669#heading-21

## vue对Array数据双向绑定的实现
- 参考：https://juejin.im/post/6844903605057617934
1. 创建一个原型指向Array.prototype 的对象arraymethods，使用Object.defineproperty对此对象的数组方法写进行监听；
2. 然后新建的数组对象原型指向arraymethods；

## vue的data为什么是函数而不是对象？
1. vue的data数据其实是vue原型上的属性，数据存在于内存中，为了保证每个实例上data数据的独立性，所以用了函数，因为如果是使用对象的话，每个vue实例的data数据都是互相影响的。
2. 同一个组件被复用多次会创建多个实例，如果是对象就会相互影响，

## nextTick
- 得到更新后的Dom，因为在视图更新时，是异步的，不能立刻得到更新后的文档，nextTick接口，是在文档更新后执行，所以能得到更新后的Dom

## vue为什么采用异步渲染
- vue是组件级更新，如果不采用异步更新，那么每次更新数据都会对当前组件进行重新渲染，为了性能，所以vue会在本轮数据更新后，在异步更新视图，核心是 nextTick.
