# CORS 策略跨域请求

## 运行方式

1. 使用node.js执行index.js文件，监听81端口；

2. 更改本地hosts文件，映射本地访问为

```
  127.0.0.1  qq.com
  127.0.0.1  hikari.com
  127.0.0.1  www.qq.com
```

3. 访问"http://hikari.com:81/hikari" ，发送Ajax请求"http://qq.com:81/qq.json" 的数据；

4. 即可实现"http://hikari.com:81/hikari" 对"http://qq.com" 的跨域请求。

## 实现方式

在后端的服务器js文件中，对访问指定地址的响应头设置以下代码：

```javascript
response.setHeader('Access-Control-Allow-Origin','http://hikari.com:81')
response.setHeader('Access-Control-Allow-Methods','GET,POST,OPTIONS,PATCH,PUT')
```

即可为指定域名开放指定的GET, POST, OPTIONS等请求权限。

## 特别说明

在OS X和Linux上可使用sudo直接监听80端口，更加简洁方便。
