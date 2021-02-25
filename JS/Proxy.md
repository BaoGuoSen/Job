#### 示例
```JavaScript
// 每次访问age属性，+1
var obj2 = {
  age: 1
}

var handler = {
  get (obj,key) {
    return key in obj ? ++obj[key] : 1
  }
}

var proxy = new Proxy(obj2, handler)
console.log(proxy.age)
```

#### 捕捉器
1. getPrototypeOf()
- Object.getPrototypeOf 方法的捕捉器。
2. setPrototypeOf()
- Object.setPrototypeOf 方法的捕捉器。
3. defineProperty()
4. has()
- in 操作符的捕捉器
5. get（）
6. set（）
7. deleteProperty()
8. ownKeys()
9. apply() 代理只能是函数
10. construct （代理构造函数）


#### proxy代理
- 代理对象后，两者指向同一对象，所做的修改将影响双方，但是在原对象进行操作不会触发捕捉器；