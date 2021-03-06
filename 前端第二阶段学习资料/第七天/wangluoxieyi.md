﻿# 网络传输协议

标签（空格分隔）： 网络开发

---
![前端学院][1]

[toc]

## 常见网络传输协议
>协议可以理解为一套`规范`,当使用的双反都遵守这套规范时,才能够实现沟通.比如对于`嘿嘿`的理解不同,带来的沟通障碍.网络协议就有更多规则,需要先干什么,再干什么

* 常见协议
    * HTTP,HTTPS超文本传输协议
    * FTP文件传输协议
    * SMTP邮件传输协议

## HTTP协议
>网站是基于`HTTP`协议的,比如我们在开发网站中经常使用的`css`,`js`,`图片`等等都是基于该协议进行传输的

* 组成部分
    * 从客户端(能够发送`HTTP`)发出的:`请求Request`
    * 从服务器返回的:`响应Response`

![http开发][2]

### 监测工具
>使用监测工具我们可以查看这些`HTTP`请求,以及编辑请求内容,重新发送等

* 浏览器
    * Chrome,Firefox开发工具
* 抓包工具
    * Fiddler,Charles

### 请求/请求报文
>请求有`客户端`发出,主要有三个组成部分:`请求行`,`请求头`,`请求主体`


![请求.jpg-108.8kB][3]

* **请求行:**
    * 请求方法:`GET`
    * 请求`URL`
    * `HTTP`协议版本

* **请求头**
    *  这里设置的主要是一些信息,包含`客户端`,`服务器`

```
User-Agent：浏览器的具体类型　　如：User-Agent：Mozilla/5.0 (Windows NT 6.1; rv:17.0) Gecko/20100101 Firefox/17.0

Accept：浏览器支持哪些数据类型　　如：Accept: text/html,application/xhtml+xml,application/xml;q=0.9;

Accept-Charset：浏览器采用的是哪种编码　　如：Accept-Charset: ISO-8859-1

Accept-Encoding：浏览器支持解码的数据压缩格式　　如：Accept-Encoding: gzip, deflate

Accept-Language：浏览器的语言环境　　如：Accept-Language zh-cn,zh;q=0.8,en-us;q=0.5,en;q=0.3

Host：请求的主机名，允许多个域名同处一个IP地址，即虚拟主机。Host:www.baidu.com

Connection：表示是否需要持久连接。Keep-Alive/close，HTTP1.1默认是持久连接，它可以利用持久连接的优点，当页面包含多个元素时（例如Applet，图片），显著地减少下载所需要的时间。要实现这一点，Servlet需要在应答中发送一个Content-Length头，最简单的实现方法是：先把内容写入ByteArrayOutputStream，然后在正式写出内容之前计算它的大小。如：Connection: Keep-Alive

Content-Length：表示请求消息正文的长度。对于POST请求来说Content-Length必须出现。

Content-Type：WEB服务器告诉浏览器自己响应的对象的类型和字符集。例如：Content-Type: text/html; charset='gb2312'

Content-Encoding：WEB服务器表明自己使用了什么压缩方法（gzip，deflate）压缩响应中的对象。例如：Content-Encoding：gzip

Content-Language：WEB服务器告诉浏览器自己响应的对象的语言。

Cookie：最常用的请求头，浏览器每次都会将cookie发送到服务器上，允许服务器在客户端存储少量数据。

Referer：包含一个URL，用户从该URL代表的页面出发访问当前请求的页面。服务器能知道你是从哪个页面过来的。Referer: http://www.baidu.com/
```

* 请求体
    *  这里是提交给服务器的数据
    *  需要注意的是,如果是往服务器提交数据,需要在请求头中设置`Content-Type: application/x-www-form-urlencoded`(在ajax中需要手动设置)

### 响应/响应报文
> 响应报文是`服务器`发回给`客户端`的.组成部分有`状态行`,`响应头`,`响应主体`

![响应.jpg-30.1kB][5]

常见相应属性
```
Cache-Control 

响应输出到客户端后，服务端通过该报文头属告诉客户端如何控制响应内容的缓存。 

下面，的设置让客户端对响应内容缓存3600秒，也即在3600秒内，如果客户再次访问该资源，直接从客户端的缓存中返回内容给客户，不要再从服务端获取（当然，这个功能是靠客户端实现的，服务端只是通过这个属性提示客户端“应该这么做”，做不做，还是决定于客户端，如果是自己宣称支持HTTP的客户端，则就应该这样实现）。

Cache-Control: max-age=3600

ETag

一个代表响应服务端资源（如页面）版本的报文头属性，如果某个服务端资源发生变化了，这个ETag就会相应发生变化。它是Cache-Control的有益补充，可以让客户端“更智能”地处理什么时候要从服务端取资源，什么时候可以直接从缓存中返回响应。

ETag: "737060cd8c284d8af7ad3082f209582d"

Location

我们在Asp.net中让页面Redirect到一个某个A页面中，其实是让客户端再发一个请求到A页面，这个需要Redirect到的A页面的URL，其实就是通过响应报文头的Location属性告知客户端的，如下的报文头属性，将使客户端redirect到iteye的首页中：

Location: http://www.google.com.hk

Set-Cookie

服务端可以设置客户端的Cookie，其原理就是通过这个响应报文头属性实现的。

Set-Cookie: UserID=JohnDoe; Max-Age=3600; Version=1

HTTP响应体：如果请求的是HTML页面，那么返回的就是HTML代码。如果是JS就是JS代码。

HTTP响应头：而设置Cookie，缓存等信息就是在响应头属性设置的。

HTTP响应行：主要是设置响应状态等信息。
```


## 常见的响应状态
![图片1.png-71.5kB][4]




  [1]: http://static.zybuluo.com/antumuFish/xfnngpb23mze67n7y3y9ir3l/desk.jpg
  [2]: http://static.zybuluo.com/antumuFish/9jiqaow7fc2ddu1u9tkzf96k/webSteps.gif
  [3]: http://static.zybuluo.com/antumuFish/o23f9i9c49b8rgzpcz8ka809/%E8%AF%B7%E6%B1%82.jpg
  [4]: http://static.zybuluo.com/antumuFish/3oes065wi64oaemk3f3vszld/%E5%9B%BE%E7%89%871.png
  [5]: http://static.zybuluo.com/antumuFish/68djvxi3xm24ud6mpx8yab75/%E5%93%8D%E5%BA%94.jpg