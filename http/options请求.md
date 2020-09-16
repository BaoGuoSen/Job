## 不会触发Options请求的称为简单请求

## 不会触发Cors预检Options请求的条件
1. 使用GET、POST、HEAD其中一种方法
2. 只使用了如下的安全首部字段，不得人为设置其他首部字段（因为cors请求会设置Origin字段，所以会触发Options请求）
- Accept
- Accept-Language
- Content-Language
- Content-Type 仅限以下三种
1. text/plain
2. multipart/form-data
3. application/x-www-form-urlencoded
