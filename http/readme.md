
## Get和Post的区别
- get用URL传参，Post将信息放在body里面
- get由于用url，而有些浏览器对url有长度限制，所以传递的信息有限，而post没有限制
- 由于地址栏是可见的，所以post比get安全
- 根据http规范，get是幂等性的，而post不是幂等性的，如果网络不好，刷新重新提交，post可能会重复修改资源（幂等性即对同一个url的多个请求会返回同一个结果，即不会对资源造成影响）。
##  Http的请求报文
1. 请求方法/URL 协议/版本
2. 请求头部（可自定义头部信息）
- Accept：浏览器能够显示的字符集
- Accept-Charset：浏览器能够显示的字符集
- Accept-Encoding：浏览器能够处理的压缩编码
- Accept-Language：浏览器当前设置的语言
- Connection：浏览器与服务器直接连接的类型
- Cookie：当前页面设置的任何Cookie
- Host：发出请求的页面所在的域
- Referer：发出请求的页面的URL
- User-Agent：浏览器的用户代理字符串
3. 请求正文
## Http的响应报文
1. 协议/版本 状态码 描述
2. 响应头（部分）
- Date：日期时间
- Server：服务器类型
- Connection：客户端与服务器的连接类型
- Content-Type：响应的文本类型
3. 响应正文
