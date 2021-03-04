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

## webpack的构建流程是怎样的
webpack的构建流程是一个串行的过程；
1. 初始化参数：从配置文件和shell语句中读取与合并参数，得出最终的参数；
2. 开始编译：用上一步得到的参数初始化Compliier对象，加载所有配置的插件，通过执行对象的run方法开始执行编译；
3. 确定入口：根据配置文件中的entry找出所有的入口文件；
4. 编译模块：从入口文件出发，调用所有配置的loder对模块进行加载，在找出该模块依赖的模块，递归此步骤，对该入口文件的所有模块都进行了处理；
5. 完成编译模块：得到了每个模块被加载之后的最终内容以及他们之间的依赖关系；
6. 输出资源：根据入口和模块之间的依赖关系，得到包含多个模块的chunk代码块，在将每个代码块转换成一个单独的文件加入到输出列表；
7. 输出完成：确定了输出内容之后，根据配置确定输出的路径和文件名，写入到文件系统；

- 在以上过程中，Webpack 会在特定的时间点广播出特定的事件，插件在监听到感兴趣的事件后会执行特定的逻辑，并且插件可以调用 Webpack 提供的 API 改变 Webpack 的运行结果。

## webpack打包优化；
1. 压缩代码：利用插件对文件进行压缩
2. 压缩图片：配置image-webpack-loder压缩图片
2. 使用CDN引入外部静态文件
3. TreeShaking:删除无用的代码；
4. 按需加载
5. 通过DLLplugin提前打包指定的类；
6. 使用高版本的webpack

## 常见loder和plugin及作用
1. loder：
- html-loder:将HTML文件导出编译为字符串，可供js识别的其中一个模块
- css-loder：解析css文件中代码；
- style-loder：将css模块作为样式导出到DOM中
- sass-loder：加载和转义sass/scss文件
- babel-loder：加载ES6+代码后使用babel转义为浏览器能够解析的版本；
- url-loder：用于加载图片资源，超过文件大小显示则返回dataurl；，用户能设置阈值，超过交给file-loder处理，没超过，会使用base64编码
- vue-loder：加载和转义vue组件；
- image-loder: 加载并压缩图片
2. plugin：
- HtmlWebpackPlugin：将所有生成的js文件引入到html中，
- HotModuleReplacementPlugin:实现模块热替换；
- imagemin-webpack-plugin：批量压缩图片；
- clean-webpack-plugin：每次打包时先清空output文件夹；
- ignore-plugin: 忽略部分文件

## 核心概念
- 入口
- 输出
- loder
- pulgin

## loder and pulgins的区别
1. loder：loder本质是一个函数，在该函数中对接收的内容进行转换，因为wb只能处理js文件，所以需要引入loder对其他类型的资源进行转换工作
2. pulgin：pulgin就是插件，去拓展wb的功能，因为wb只能利用loder去转换某些类型的模块，所以需要引入pulgins去执行范围更广的操作，比如打包优化，压缩，热加载等。
