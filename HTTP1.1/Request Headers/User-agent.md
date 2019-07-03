# User-Agent





**User-Agent** 首部包含了一个特征字符串，用来让网络协议的对端来识别发起请求的用户代理软件的应用类型、操作系统、软件开发商以及版本号



格式如下：

```http
user-agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/74.0.3729.169 Safari/537.36
```

- ***Mozilla/5.0*** 是一个通用标记符号，用来表示与 Mozilla 兼容，这几乎是现代浏览器的标配。
- **platform** 用来说明浏览器所运行的原生系统平台（例如 Windows、Mac、Linux 或 Android），以及是否运行在手机上。搭载 Firefox OS 的手机仅简单地使用了 "Mobile" 这个字符串；因为 web 本身就是平台。注意 ***platform*** 可能会包含多个使用 "; " 隔开的标记符号。参见下文获取更多的细节信息及示例。
- **rv:geckoversion** 表示 Gecko 的发布版本号（例如  "17.0"）。在近期发布的版本中，**geckoversion** 表示的值与 **firefoxversion** 相同。
- **Gecko/geckotrail** 表示该浏览器基于 Gecko 渲染引擎。
- 在桌面浏览器中， ***geckotrail***  是固定的字符串 "20100101" 。
- ***Firefox/firefoxversion*** 表示该浏览器是 Firefox，并且提供了版本号信息（例如  "17.0"）。

