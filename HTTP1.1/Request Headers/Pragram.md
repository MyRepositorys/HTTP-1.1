# Pragma



### 该字段只会出现在请求头中



> ### pragma 的作用



* pragma 该字段是<code>http/1.0</code>  中的字段，在1.1的版本中也保留了，为了兼容1.0，

* 该字段的唯一的值就是 <code>no-cache</code> 指明了，不要代理缓存的资源的副本，

* 在<code>HTTP/1.1</code> 中只要在请求头中设置

  * ```http
    Cache-Control:no-cache
    ```

  * 支持<code>HTTP/1.1</code> 的中间代理就不会讲缓存的资源的副本直接发给客户端

由于客户端与服务器之间可能存在多个代理，而每个代理所支持<code>HTTP</code> 版本不同，有的只支持1.0，有的只支持1.1，所以为了能保证客户端的意愿能正常的表达，一般在请求头中会这样设置

```http
Cache-Control:no-cache
Pragma:no-cache
```



