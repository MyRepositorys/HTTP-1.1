# If-Modified-since





### 这个请求头是干什么的



这个请求头是用来对资源进行服务器再验证用的，会读取浏览器已经缓存的响应中的响应头<code>Last-Modified</code>作为本次服务器再验证<code>If-Modified-since</code> 参数的值，

请求头如下：

```http
:authority: www.cnblogs.com
:method: GET
:path: /baihuitestsoftware/articles/6101239.html
:scheme: https
accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3
accept-encoding: gzip, deflate, br
accept-language: zh-CN,zh;q=0.9,en;q=0.8
cache-control: max-age=0
dnt: 1
if-modified-since: Wed, 03 Jul 2019 13:10:33 GMT
upgrade-insecure-requests: 1
user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36
```



响应头如下：

```http
cache-control: private, max-age=10
content-encoding: gzip
content-type: text/html; charset=utf-8
date: Wed, 03 Jul 2019 13:11:24 GMT
expires: Wed, 03 Jul 2019 13:11:34 GMT
last-modified: Wed, 03 Jul 2019 13:11:24 GMT
server: Tengine
status: 200
vary: Accept-Encoding
x-frame-options: SAMEORIGIN
x-ua-compatible: IE=10
```



当刷新的时候浏览器在请求头中添加

```http
cache-control: max-age=0
if-modified-since: Wed, 03 Jul 2019 13:10:33 GMT
```

其中<code>if-modified-since</code> 是从上次对响应的缓存中提取的，语义是如果该资源在<code>if-modified-since</code>  指定的时间后发生了改变，请把最新的资源发送给我



如果服务器发现资源并没有在<code>if-modified-since</code>  指定的时间后发生改变 服务器端会返回一个状态码

```http
status:304 Not Modified
```

服务器会将新的