## 目录
- url参数提取为对象
- 深拷贝函数
- 防抖
- 节流
- Ajax
- instanceof实现
- 数组扁平化
- 大数相加
- 私有变量
- 最长公共子串
- 最长回文子串
- 36进制求和
- new的模拟实现
- 全排列
## url参数提取为对象
```JavaScript
function demo(str) {
  let obj = {};
  let newstr = str.split("?")[1];
  console.log(newstr);
  let arr = newstr.split("&");
  for(let i = 0;i<arr.length;i++) {
    let newarr = arr[i].split("=");
    console.log(newarr);
    obj[newarr[0]] = newarr[1];
    
  }
  return obj;
}
console.log(demo("https://www.nowcoder.com/discuss/193592?type=post&order=time&pos=&page=1&channel=666&source_id=search_post"));
```
## 深拷贝函数
```JavaScript
JSON.parse(JSON.stringify(obj);
function deepclone(obj) {
  if(tpyeof obj !== "object" || obj === null ) return ;
  let newobj = obj instanceof Array ? []:{};
  for(let key in obj) {
    if(obj.hasOwnProperty(key)) {
      newobj[key] = typeof obj[key] === "object" ? deepclone(obj[key]) : obj[key];
    }
  }
  return newobj;
}
```
## 防抖
```JavaScript
function debounce(fn,wait) {
  let timeout;
  return function () {
    if(timeout) clearTimeout(timeout);
    timeout = setTimeout(function () {
      fn.apply(this,arguments);
    },wait);
  }
}
```
## 节流
```JavaScript
function throttle(fn,wait) {
  let pre = 0;
  return function () {
    let date = Date.now();
    if(date - pre > wait) {
      fn.apply(this,arguments);
      pre = date;
    }
  }
}
```
## Ajax
```JavaScript
var xhr = new XMLHttpRequest();
xhr.onload = function () {
  if(xhr.readyState === 4 && xhr.status === 200)
    	console.log(xhr.responseText);
  else 
    	console.log(xhr.status);
}
xhr.open("get","url",false);
xhr.send();
```
## instaceof实现
```JavaScript
function instace_of(Sub,Super) {
  while(true) {
    if(Sub.__proto__ === null) return false;
    if(Sub.__proto__ === Super.prototype) return true;
    Sub.__proto__ = Sub.__proto__.__proto__;
  }
}
```
## 数组扁平化
```JavaScript
function flatten(arr) {
  while(arr.some(item => Array.isArray(item))) {
    arr = [].concat(...arr);
  }
}
arr.flat(Infinity);
}
```
## js大数相加
```JavaScript
function bigadd(x,y) {
    x = x.split("");
    y = y.split("");
    let res = [];
    let carry = 0;
    while(x.length !==0 && y.length !==0) {
        let temp = parseInt(x.pop()) + parseInt(y.pop()) + carry;
        res.unshift(temp%10);
        carry = Math.floor(temp/10);
    }

    while(x.length !== 0) {
        let temp = carry + parseInt(x.pop());
        res.unshift(temp%10);
        carry = Math.floor(temp/10);
    }
    while(y.length !== 0) {
        let temp = carry + parseInt(y.pop());
        res.unshift(temp%10);
        carry = Math.floor(temp/10);
    }
    
    return res.join("");
}
console.log(bigadd("123456789987654321","500381199802034135"));
```
## 私有变量
```JavaScript
const Example = (function(name) {
  var _private = 'ddd';

  class Example {
    constructor(name) {
      _private = name;
    }
    getName() {
      return _private;
    }
  }

  return Example;

})();

var ex = new Example("name");

console.log(ex.getName()); // private
console.log(ex._private); // undefined
```
## 最长公共子串
```JavaScript
function demo(str1,str2) {
  let m = str1.length;
  let n = str2.length;
 let index;
  let dp = [];   
  var res = 0;
  for(let i = 0;i<=m;i++)
  {
    dp[i] = [];
    for(let j = 0;j<=n;j++) {
      if(i === 0 || j === 0) {
        dp[i][j] = 0;
        continue;
      }
      if(str1[i-1] === str2[j-1]) {
        dp[i][j] = dp[i-1][j-1]+1;
        if(dp[i][j]>res){
          res = dp[i][j];
        	index = i-1;
          
        }
      }
      else 
        dp[i][j] = 0;
    }
  }
  console.log(index);
          console.log(res);
  console.log(str1.slice(index-res+1,index+1));
}
demo("abcde","bddfabcde4543564");
```
## 最长回文子串
```JavaScript
var longestPalindrome = function(s) {
    if(s.length === 0) return "";
    let dp = [];
    let len = s.length;
    var res = "";
    //从后往前，使d[i][]依赖dp[i+1][];
    for(let i = len - 1;i>=0;i--) {
        dp[i] = [];
        for(let j = i;j<len;j++) {
            if(i === j) dp[i][j] = true;
            else if(j - i === 1 && s[i] === s[j]) dp[i][j] = true;
            else if(s[i] === s[j] && dp[i+1][j-1]) dp[i][j] = true;

            if(dp[i][j] && j-i+1 > res.length)
                res = s.slice(i,j+1);
        }
    }
    return res;
};
```
## 36进制求和
```JavaScript
function demo(str1,str2) {
  let res = 0;
  let a = parseInt(str1,36);
  let b = parseInt(str2,36);
  res = a+b;
  return res.toString(36);
}
console.log(demo("a",1));
```
## new的模拟实现
```JavaScript
function person() {
  this.name = "test";
}
function _new() {
  let obj = new Object();
 
  let _constructor = [].shift.call(arguments);
  
  obj.__proto__  = _constructor.prototype;
  
  let res = _constructor.apply(obj,arguments);
  return typeof res === 'object' ? res:obj;
}
let obj = _new(person);
console.log(obj.name);
```
## 全排列
```JavaScript
function dfs(list,templist,nums) {
  if(nums.length === templist.length) {
    list.push([...templist]);
  }
  for(let i = 0;i<nums.length;i++) {
    if(templist.includes(nums[i])) continue;
    templist.push(nums[i]);
    dfs(list,templist,nums);
    templist.pop();
  }
  return list;
}
function permute(nums) {
  let list = [];
  dfs(list,[],nums);
  return list;
}
console.log(permute("123"));
```
