
## cookie机制
1. Domain cookie的作用域名；
2. Path cookie的作用路径；
3. Expires 和 Max-Age cookie的存在时间；
4. HttpOnly 能否通过js脚本获得cookie； （防止 跨域请求攻击）
5. Secure 设置后cookie只能在https协议中通信；
6. SameSite 能否跨站通信；（防止 跨域请求伪造）

## session机制
1. 存储在服务端，相比于cookie安全性更高；
2. 依赖与cookie，通过cookie里的 sessionid 来用户状态（如果cookie被禁用，通过url或者隐藏表单字段）；
3. 使用类似于散列表的结构来存储值；

## 两者的不同
1. 安全性：session的安全性更高；
2. 有效期：cookie的时间可以很长，而session一般不长，因为如果累积session很多会给服务器造成很大的压力；
