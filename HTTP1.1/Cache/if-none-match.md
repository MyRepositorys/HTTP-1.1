# if-none-match



#### 为什么需要 if-none-match

在服务器上可能对某个资源进行重复性的读写，有可能实际内容没发生变化，但是每一次读写都会更新该文件的最后更新时间



所以服务器上还有对文件的版本的描述信息，<code>Etag</code> 标签，当资源发布者，实际修改了资源后会更改<code>Etag</code> 的值

用来说明修改的版本，



什么时候会使用该资源去服务器进行再验证呢？

当响应中有<code>Etag</code> 字段的时候，客户端在进行服务器再验证，就可以使用<code>if-modified-since</code> 和<code>if-none-match</code> 组合使用，来验证资源的有效性



当服务器相应只返回<code>last-Modified</code> 或者只返回<code>Etag</code> ，那么客户端就只能用其中一个，当响应中两着都返回后，客户端在向服务器验证的时候必须都使用

