# Range



所谓的范围请求，一般用于网络下载中，下载中断，客户端想要恢复下载而又不想从头开始下载，这个时候客户端会尝试进行范围请求，

在请求头中添加Range 字段，指定请求资源的某些字节以后的数据，或者一段数据

格式如下：

```http
Range:bytes=1500-
```



范围请求也经常搭配条件请求一起使用，<code>if-range</code>  该字段的值可能是<code>Etag</code> 值，也可能是个<code>Last-modified</code>

当<code>if-range</code> 的值是<code>Etag</code> 值的意思就是，资源是否发生改变，如果未发生改变，请求服务器将指定的资源部分返回，

当<code>if-range</code> 携带的是<code>last-modified</code> ，则匹配资源最后的更新时间，如果未更新则返回指定的资源

