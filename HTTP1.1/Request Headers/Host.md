# Host



> ### 为什么需要Host 字段



<code>HOST</code> 字段只会出现在请求头中，为什么请求头中需要这个字段呢？

在请求中，根据很具<code>URL</code> 解析出<code>HOST</code>，然后向域名域名服务器发起请求，解析<code>HOST</code> 。域名服务器解析后会传回

<code>HOTS</code>服务器的<code>IP</code> 地址，然后客户端根据该地址向服务器发起请求，



<strong>但是</strong> 一台真实的服务器上可能存在多个域名，也就是说，该服务器可以处理A 域名的请求响应，也可以处理B域名的请求响应，

那么客户端在根据<code>IP</code> 地址可以和这个服务器建立连接，但是该服务器不知道你要访问的域名是那个，也就无法调用相应的<code>HTTP Server</code> 处理该请求，



所以客户端在发起请求的时候会带上<code>HOST</code>字段，客户端也不知道所访问的服务器上是否存在多个不同域的<code>HTTP Server</code>

