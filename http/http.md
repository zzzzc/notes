## HTTP Messages

![HTTP Messages](./images/HTTPMsgStructure2.png)

request message

```
<method> <request-URL> <version>
<headers>
  
<entity-body>
```

response message

```
<version> <status> <reason-phrase>
<headers>

<entity-body>
```

### methods

1. 安全方法:GET 和 HEAD

2. HEAD的作用 : 
  * 在不获取资源的情况下了解资源的情况（比如，判断其类型）； 
  * 通过查看响应中的状态码，看看某个对象是否存在；
  * 通过查看首部，测试资源是否被修改了。

3. POST 用于向服务器发送数据。PUT 用于向服务器上的资源（例如文件）中存储数据。

4. TRACE 请求会在目的服务器端发起一个“环回”诊断。行程最后一站的服务器会弹回一条

5. OPTIONS 方法请求 Web 服务器告知其支持的各种功能。

6. DELETE 方法所做的事情就是请服务器删除请求 URL 所指定的资源。

7. 扩展方法: LOCK 、MKCOL 、COPY 、 MOVE...


### status

1. 100 Continue: 客户端在发送实体之前查看一下服务器是否会接受。 eg:
  ```
  request headers : Expect: 100-continue -> 
  response status : 100 continue -> 
  new request -> 
  response status : 200 ok
  ```

2. 304 Not Modified: 
  * Request: 

  ``` HTTP
  GET / HTTP/1.1
  ...
  If-Modified-Since: Fri, Oct 3 1997 02:16:00 GMT
  ```

  * Response:

  ``` HTTP
  HTTP/1.1 304 Not Modified
  ```


### headers

| type  |  contents  |
|---|---|
| 1. 通用首部 |  Connection/ Date / MIME-Version / Trailer /  Transfer-Encoding / Update / Via | 
| 1.1 通用缓存首部 |  Cache-Control  / Pragma |
| 2. 请求首部 |  Client-IP /  From / Host / **User-Agent** / Referer / UA-Color / UA-CPU / UA-Disp / UA-OS / UA-Pixels  |
| 2.1 Accept首部 | Accept / Accept-Charset / Accept-Encoding / Accept-Language / TE |
| 2.2 条件请求首部 |  Expect / If-Match / **If-Modified-Since** / If-None-Match / If-Range / If-Unmodified-Since / Range | 
| 2.3 安全请求首部 |  Authorization /  Cookie  |
| 2.4 代理请求首部 | Max-Forward / Proxy-Authorization / Proxy-Connection | 
| 3. 响应首部 | Age / Public / Retry-After / Server / Title / Warning |
| 3.1 协商首部 | Accept-Ranges / Vary |
| 3.2 安全响应首部 | Proxy-Authenticate / Set-Cookies / WWW-Authenticate |
| 4. 实体首部 | Allow / Location |
| 4.1 内容首部 |  Content-Base /  Content-Encoding / Content-Language / Content-Length / Content-Location / Content-MD5 / Content-Range / Content-Type |
| 4.2 实体缓存首部 |  ETag / Expires / Last-Modified |
| 5. 扩展首部 | 其他 |

> tips: 将长的首部行分为多行可以提高可读性，多出来的每行前面至少要有一个空格或制表符（tab）。

## Connection

http请求步骤：

```
1. 从url解析主机名
2. 根据主机名查询ip地址
3. 根据ip和端口建立tcp连接
4. 客户端发送请求message
5. 服务端发送响应报文
6. 浏览器关闭连接
```

### http连接优化
1. 并行连接
2. 持久连接
3. 管道化连接

### web服务器做了什么
1. 接受客户端连接
2. 接受请求报文
3. 请求处理
4. 对资源的映射和访问
5. 构建响应
6. 发送响应
7. 记录日志

## 缓存

Cache-Control: 

1. no-store
2. no-cache
3. max-age
4. must-revalidate

## http 2.0


