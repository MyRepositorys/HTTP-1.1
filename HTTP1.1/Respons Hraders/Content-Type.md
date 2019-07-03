# Content-Type



* 这是个响应头，作用是告诉客户端响应正文的内容类型

  ```http
  Content-Type: text/html;
  ```

  客户端的浏览器是依据该响应头的值去调用相应的应用程序去读取显示<code>HTTP</code>  的正文的





* 该响应头不只一个值，最常见的还带有<code>charset</code>  

  ```http
  Content-Type: text/plain; charset=UTF-8
  ```

  <code>charset</code> 的值的作用是告诉浏览器以什么编码方式读取数据转为字符





* 关于<code>MIME</code>

  <code>MIME</code> 的全称是<code>Multipurpose Internet Mail Extensions</code> 的缩写，翻译就是多目的 因特网邮件扩展

  他的作用是，指明响应正文中的文件类型，如文本文件，多媒体文件，应用程序，ZIP 等

  <code>MIME</code> 的值有几百多种，在<code>Content-Type</code> 中显示的是这种格式：

  ​		<code>type/subtype</code>  父类型在前面，子类型在后面

