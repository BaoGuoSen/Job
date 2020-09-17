## Fetch 与 XMLHttpRequest的不同
1. 接到一个错误的HTTP状态码时，从fetch返回的Promise不会被标记为reject，比如（404，500），仅当网络故障或者请求被阻止时，才会被标记为reject
2. fetch默认不会带cookie，需要添加配置项；
3. fetch不支持abort，不支持超时控制，
4. fetch没有办法原生检测请求的进度，
