#### 首先是dns解析（将网址转为ip地址）
- dns预解析，cdn都发生在这一阶段
1. 操作系统会先查找hosts文件是否有记录，有则返回
2. 没有就去本地dns解析器上有没有缓存， 有则返回
3. 还没有，就去根服务器查询
4. 没有，就去一级域名服务器，二级域名服务器，直到找到id地址

#### tcp三次握手
- 有可能是https（ssl握手），或者websocket握手，转化应用层协议
1. websocket握手，
- 在三次握手的基础上，在发送一个请求，新增头部字段
- Upgrade: websocket
- Connection: Upgrade
- 然后服务端响应101状态码，表示转化成功，之后就没http的事了

2. ssl握手
- 详情去往 =》https目录下的readme

3. 三次握手
- client 发送SYN请求，seq = x status： SYN-send
- Server 收到，发送SYN，ACK请求，ack = x+1,seq = y SYN-recvid
- Client 发送ACK，ack = y+1 Established

#### client发送请求
- 有http缓存，强缓存，协商缓存在这一阶段

#### server响应回复
- 状态码记清楚

#### 接收文件并解析
1. 构建DOM树，从上到下解析HTML文档生成DOM节点树
- 遇到script标签，会判断是否存在 async 或者 defer属性
  - async： 并行下载文件，下载完成后执行js
  - defer： 并行下载文件，文档解析完成后执行
- 遇到link下载并解析css， 生成cssom规则树
  - link引用
  - style标签
  - 内联样式
2. 生成渲染树，DOM树+CSSOM树
3. 重排（回流） ： 根据生成的渲染树，得到节点的几何信息（位置，尺寸）
4. 重绘 ： 根据渲染树，和回流得到节点的几何信息，样式，将节点转换成屏幕上的实际像素；
5. 将像素发送给GPU绘制，合成图层，展示在页面上

#### 四次挥手
1. Client 发送FIN请求，seq = u， FIN-wait1
2. Server 收到，发送ACK请求 ack= u+1，close-wait， Client 收到变为FIn-wait2
3. Serve 数据处理完毕，发送FIN，ACK请求，ack = u+1，seq = k， LAST-ack
4. CLient 收到FIN，发送ACK，ack = k+1，seq = v， 等待Time-wait（2MSL)后关闭连接,Server 收到后立即关闭连接

