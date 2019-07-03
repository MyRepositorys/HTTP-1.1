# Accept





##### 这个字段只会出现在请求头中，表示所请求服务器中的资源，服务器以什么类型返回资源



格式如下：

```http
Accept:text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
```

该资源表示希望服务器反向资源的类型是这些，<code>text/html</code>,<code>application/xhtml+xml</code>,<code>application/xml</code> 

其中后面的<code>q=0.9</code> 表示权重，

所谓的权重，就是客户端最希望服务器返回资源的类型，最优先的类型，其中 <code>q=1</code> 表示权重最大，

上面的<code>* / *</code> 比   <code>q=0.1</code> 还小，用于占位用的，上面的有三种类型，其中有0.9，0.8，还有中间的类型，表示无所谓权重不权重的，就用这个代替





### 与请求头中Accept,对应的响应头中的Content-Type



<code>Content-Type</code> 该字段表示的是，响应返回的数据的类型，

* 在客户端接收到响应后，首先以响应头<code>Transfe-Encoding</code> 或者<code>Content-Encoding</code> 标注的方式进行解压缩，或者组装分块，

* 然后以响应头中<code>Content-Type:charset=xxx</code>的字符集编码方式，读取字符，
* 然后以<code>Content-Type:xxx</code> 中标注的响应文件的类型(<code>text</code>,<code>css</code>,<code>html</code>,<code>jpg</code>)去调用相应的程序去打开显示数据
* <code>Content-Language：xxx</code> 标注的字符显示的语言类型(中文，应为，繁体中文) 等只具有参考价值

