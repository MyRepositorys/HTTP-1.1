# Accept-Encoding





#### 这个字段只会出现在请求头中，表示客户端支持的对响应正文的压缩/传输格式



格式如下：

```http
Accept-Encoding: gzip, deflate, br
```

表示客户端能对这些压缩编码的响应正文进行解码，



响应正文中也会告诉，客户端请以这种编码格式进行解码，

```http
content-encoding:br
```

