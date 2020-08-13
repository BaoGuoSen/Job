##### 参考链接：https://juejin.im/post/6844903873518239752

## CDN
<img src="https://user-gold-cdn.xitu.io/2019/6/24/16b87f0340a17453?imageView2/0/w/1280/h/960/format/webp/ignore-error/1" 
alt="cdn过程图" width="800" height="613" align="bottom" /><br>
1. 用户发起http请求，通过本地DNS获取请求地址的ip地址
2. 经过本地DNS系统解析，DNS系统最终会将域名的解析权交给CNAME指向的CDN专用DNS服务器；
3. 专用DNS服务器将CDN的全局负载均衡设备的ip地址返回给客户端；
4. 客户端向全局负载均衡服务器发送请求，全局负载均衡设备根据用户的ip地址及请求内容
选择一台用户所属区域的区域负载均衡设备的ip地址返回；
5. 区域负载均衡设备根据用户的ip地址，请求内容，各个缓存服务器的负载情况，将最优的一台缓存服务器的ip地址返回给客户端
6. 然后客户端向该缓存服务器发送请求即可获得响应内容；


