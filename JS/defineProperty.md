#### 属性详解
1. configurable
- 能否被删除后重新定义
2. enumerable
- 能否可枚举
3. writable
- 能否被赋值运算符改变
4. value
- 改属性对应的值
5. get
- 访问改属性时会调用该函数
6. set
- 修改属性时会调用该函数

#### 属性默认值
- 拥有布尔值的键 configurable、enumerable 和 writable 的默认值都是 false。
- 属性值和函数的键 value、get 和 set 字段的默认值为 undefined。

#### 示例
```JavaScript
var obj = {
}
var age = 1
Object.defineProperty(obj, 'age', {
  // configurable: true, 
  // enumerable: true,
  // writable: true,
  // value: 1,
  // value or writable与get和set不能共存，一定注意，会产生冲突，会报错；
  get () {
    age++
    return age
  },
  set (val) {
    age = val
  }
})
obj.age
console.log(obj.age)
```