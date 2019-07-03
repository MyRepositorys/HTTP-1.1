# Connection





> ### Connection 请求头/响应头

​	

​	Connection字段既可以用在请求头中，也可以用在响应头中，根据Connection字段不同的值，有不同的语义





> ### 控制不再转发给代理的字段

​	

为什么会有控制不再转换给代理字段这个东西呢？



首先需要从<code>HTTP/1.0</code> 中的<code>Connection:keep-Alive</code> 说起，

* 在<code>HTTP/1.0</code> 中，如果客户端在一次请求中设置了响应头<code>Connection:keep-Alive</code>
* 那么服务器在接收到该请求后，如果同意保持持久链接，就会在响应中设置一个响应头<code>Connection:keep-Alive</code>如果服务器不同持久链接，就是不设置该响应头
* 如果客户端收到响应中，在响应头中发现<code>Connection:keep-Alive</code> ，则认为服务器同意建立持久链接，那么客户端，可能会基于该持久链接发送，多条请求，或者服务器不同意持久链接，那么客户端浏览器会在处理完该响应后关闭此链接





但是有一个问题可能会出现，如果客户端与服务器之间存在哑代理

* 首先说明代理，代理相对于客户端来说就是<code>HTTP Server</code>, 相对于真正的<code>HTTP Server</code> 来说，代理就是个客户端，所以客户端也不知道自己发起请求的是代理还是<code>HTTP Server</code> 而，<code>HTTP Server</code> 也不知道向自己发起请求的是客户端还是代理
* 什么是哑代理呢？ 所谓的哑代理就是就是将数据从一个连接传到另一个连接里，并不会对首部的数据做任何处理
* 当客户端与<code>HTTP Server</code> 基于<code>HTTP/1.0</code> 的协议想要建立一个持久链接，
* 那么当客户端发起请求后，哑代理转发了这个请求，并没有做任何处理，服务器接收到请求后，同意了持久链接
* 那么当客户端发起第二个请求的时候，哑代理会忽略该请求，为什么呢？
* 因为哑代理不知道上次连接后建立了持久连接，哑代理一直等着服务器与自己断开连接，认为客户端不会再向自己发送任何数据，所以会忽略客户端的数据，
* 那对于真正的客户端与<code>HTTP Server</code>  来说，客户端认为服务器明明同意了持久链接，为什么不响应我第二次的请求，而服务器还在一直等待客户端发来的第二个请求(被哑代理给忽略掉了)











> ### 管理持久连接



* 在<code>Http/1.0</code>  中 客户端发起一个请求之前，都要经过一次<code>TCP/IP 三次握手</code> 的动作，<code>Http Server</code>  在响应后就会在响应头中设置

  ```http
  Connection:close
  ```

  而且会关闭本次<code>TCP/IP</code>连接，也就是说客户端与服务器之间每次<code>HTTP</code> 的交互都要经过三次握手，首先三次握手是很浪费时间和资源的，而且现在的一个页面可能需要发起几十个<code>Http</code> 请求，也就是说，这种通讯方式是很浪费资源和时间的，

  

* 在<code>Http/1.1</code> 协议中 不再是一次<code>Http</code> 请求一次连接了，而是多个请求基于一个<code>Tcp/id</code> 连接上，1.1版本的协议默认是持久连接的，当服务器或者客户端想断开连接是会设置Connection=close 

  ```http
  connection:close
  ```

