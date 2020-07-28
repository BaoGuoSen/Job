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
function bigadd(str1,str2) {
  let maxlen = 0;

  if(str1.length>str2.length) {
    maxlen = str1.length;
    let flag = str1.length - str2.length
    for(let i = 0;i<flag;i++) {
      str2 = 0+str2;
    }
  }
  else if(str1.length<str2.length) {
    maxlen = str2.length;
    let flag = str2.length - str1.length
    for(let i = 0;i<flag;i++) {
      str1 = 0+str1;
    }
  }
     
  let num1 = str1.split("");
  let num2 = str2.split("");
 
  let res = [];
  let carry = 0;
  for(let i = maxlen-1;i>=0;i--) {
    let temp = parseInt(num1[i])+parseInt(num2[i]);
   
    res.unshift(temp%10+carry);
    carry = parseInt(temp/10);
    
  }
  return res.join("");
}
console.log(bigadd("343534564564565462233434344534543","123676575675675675675"));
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
        	index = i;
        }
      }
      else 
        dp[i][j] = 0;
    }
  }
  console.log(str1.slice(index - res,res));
}
demo("abcde","bddfabcdee");
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

