# 1. Ajax基础
Ajax是异步的js和XML。简单来说，就是说那个XMLHttpRequest对象和服务器通信

## 1.1 axios库
- 引入axios库，axios.js
- 使用axios函数
  - 传入配置对象
  - 使用.then回调函数接收结果，并做后续的处理
```javascript
<script src="https://cdnjs.cloudflare.com/ajax/libs/axios/1.6.2/axios.min.js"></script>
    <script>
        axios({
            method: 'get',
            url: 'http://hmajax.itheima.net/api/province'
        }).then(result => {
            console.log(result)
        })
    </script>
```
## 1.2 url（uniform resource locator）介绍
以`http://hmajax.itheima.net/api/province`为例，分成三个部分：
- `http`表示协议
- `hmajax.itheima.net`表示域名
- `api/province`表示资源路径

### 1.2.1 URL查询参数
浏览器提供给服务器的额外信息，让服务器返回浏览器想要的数据。如`http://hmajax.itheima.net/api/province?参数名1=值&参数名2=值2`

### 1.2.2 常用请求方法
- GET，获取数据
- POST，提交数据
- PUT，修改数据（全部）
- DELETE，删除数据
- PATCH，修改数据（部分）


### 1.2.3 axios请求配置
- url：请求的URL网址
- method：请求的方法，get可以省略（不区分大小写）
- data：提交的数据（使用post请求的时候使用，如果使用get请求改成params）

### 1.2.4 axios错误处理
场景：重复注册相同的账号，遇到报错信息
```javascript
axios(
).then(成功回调).catch(失败的回调)
```

### 1.2.5 http协议-请求报文
- http协议：规定了浏览器发送以及服务器返回内容的格式
- 请求报文：浏览器按照http协议要求的格式，发送给服务器的内容
    - 请求行：请求方法，URL，协议，报文第一行
    - 请求头：用键值对的格式携带的附加信息，比如`Content-Type: application/json`
    - 空格行
    - 携带的信息

### 1.2.6 http协议-响应报文
- http协议：规定了浏览器发送以及服务器返回内容的格式
- 响应报文：
  - 响应行（状态行）：协议，http响应状态码，状态信息
  - 响应头：以键值对的格式携带的附加信息
  - 空行：分割响应头，空行之后就是服务器返回的资源
  - 响应体：返回的资源

### 1.2.7 http响应状态码
- 1xx，表示信息
- 2xx，表示成功
- 3xx，重定向信息
- 4xx，表示客户端错误
- 5xx，表示服务端错误

## 1.3 接口文档
描述接口的文章，使用ajax和服务器通信的时候，使用的URL，请求方法，以及参数


## 1.4 form-serialize插件
`serialize(form, {hash: true, empty: true})`，后面的字典表示配置，hash设置为true则为js对象，hash配置为false则为查询字符串；empty为true则表示获取空值，false为不获取空值
