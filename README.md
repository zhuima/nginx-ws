nginx-ws-demo
=============


[TOC]


### 一、nginx负载均衡websocket注意事项

- 和普通代理不一样的地方

```python
proxy_set_header Upgrade $http_upgrade;
proxy_set_header Connection "upgrade";
```

### 二、参考文档

[配置 Nginx 反向代理 WebSocket](https://www.hi-linux.com/posts/42176.html)

[神策服务转发配置](https://www.sensorsdata.cn/manual/data_import_nginx.html)

### 三、使用方式

```python
npm --registry=https://registry.npm.taobao.org install ws
cd ws
node server.js
# 如果想实现负载，复制ws目录，然后修改下对应的端口即可
```

### 四、测试

- npm --registry=https://registry.npm.taobao.org install wscat
- cd ~/node_modules/wscat/
- ./bin/wscat --connect ws://yourdomain
- send message test
- 查看服务器端的日志


### 五、关于ip_hash

- 有些文档表示一定要使用ip_hash，确保数据的有序，但是没有验证
- 另外就是ip_hash就是统一客户端的请求始终会落到后端的其中一个节点上，所以要特别注意


