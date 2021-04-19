#### why？
- localstorage，sessionstoreage都有着同源限制，不同域之间不可相互通信
- 利用iframe和postmessage即可跨域存储
- iframe为想要存储的域，嵌套在非同源域下，父页面通过window.frames[0].postmessage，这样就转换为同源页面的通信了，可以用广播或者storage事件