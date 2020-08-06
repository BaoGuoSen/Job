## HMR
<img src="https://github.com/BaoGuoSen/Job/blob/master/imgs/Webpack%E7%83%AD%E6%9B%B4%E6%96%B0.png" alt="图片替换文本" width="800" height="613" align="bottom" />

1. webpack监听源文件的变化，会触发webpack重新编译
2. 每次编译会产生hash值，新的json文件，新的模块代码js文件；编译完成会通过sockjs向客户端推送hash值；
3. 客户端的webpack-dev-server会收到这个hash值，和之前对比
- 一致则走缓存；
- 不一致则判断是否支持热更新
- 如果支持热更新，则通过ajax和jsonp向服务器获得新的json文件，
- 不支持则刷新浏览器
4. 通过hotmodule插件更新已修改资源；
