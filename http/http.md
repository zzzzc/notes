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

1. 通用首部 既可以出现在请求报文中，也可以出现在响应报文中。 
2. 请求首部 提供更多有关请求的信息。 
3. 响应首部 提供更多有关响应的信息。 
4. 实体首部 描述主体的长度和内容，或者资源自身。 
5. 扩展首部 规范中没有定义的新首部。

> tips: 将长的首部行分为多行可以提高可读性，多出来的每行前面至少要有一个空格或制表符（tab）。
