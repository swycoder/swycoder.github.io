---
title: 计算机网络基础
excerpt: |
   git常见命令
category:  git常见命令
feature_image: "https://picsum.photos/2560/600?image=872"
---
## 计算机网络基础

TCP（传输控制协议）协议保障数据可靠传输，即保证不丢失数据，是传输层中的一个可靠的、面向连接的协议。
UDP（用户数据报协议）传输层中一个不可靠的、无连接的协议。UDP类似于广播。
IP协议：网际层的协议，提供逻辑寻址和路由选择功能。

HTTP协议是Hyper Text Transfer Protocol（超文本传输协议）是用于从万维网服务器传输超文本到本地浏览器的传送协议。是一个基于TCP/IP通信协议来传递数据，是一个属于应用层的面向对象的协议。
```

Get请求格式：
GET / HTTP/1.1（请求行）
（空行必须）
Host    img.mukewang.com
User-Agent  Mozilla/5.0
Accept-Encoding gzip, deflate, sdch
Accept-Language zh-CN,zh;q=0.8 （请求首部Headers）

Post请求格式：
POST /login HTTP/1.1（请求行）
（空行必须）
Host    img.mukewang.com
User-Agent  Mozilla/5.0
Accept-Encoding gzip, deflate, sdch
Accept-Language zh-CN,zh;q=0.8（请求首部Headers）

username=123&pass=123（请求体）
响应格式：
HTTP/1.1 200 OK（状态行）
Content-Length: 5814
Last-Modified: Sun, 09 Dec 2018 12:35:40 GMT
Content-Length: 5814
Server: http-kit
Date: Sat, 16 Feb 2019 08:20:40 GMT （消息报头）
（空行必须）
<!DOCTYPE html>
<html lang="en">
<head>（响应正文）
```
##响应状态码：
1XX：指示消息
2XX：成功
3XX：重定向，要用到消息报头的Location字段的值做跳转（浏览器自动完成）
4XX：客户端错误
5XX：服务器错误

##HTTP请求方法
HTTP1.0定义了三种请求方法： GET, POST 和 HEAD方法。
HTTP1.1新增了五种请求方法：OPTIONS, PUT, DELETE, TRACE 和 CONNECT 方法。
```
GET     请求指定的页面信息，并返回实体主体。
HEAD    类似于get请求，只不过返回的响应中没有具体的内容，用于获取报头。普遍用于校验资源存不存在。
POST    向指定资源提交数据进行处理请求（例如提交表单或者上传文件）。数据被包含在请求体中。POST请求可能会导致新的资源的建立和/或已有资源的修改。
PUT     从客户端向服务器传送的数据取代指定的文档的内容。
DELETE  请求服务器删除指定的页面。
CONNECT HTTP/1.1协议中预留给能够将连接改为管道方式的代理服务器。
OPTIONS 允许客户端查看服务器的性能。
TRACE   回显服务器收到的请求，主要用于测试或诊断。
```
1. Get请求只用于获取资源，Post请求用于修改或添加服务器上的资源。例：用户注册和下订单一定用Post，获取物品信息一定用Get。
2. 虽说能用Get请求来发送数据到服务器来完成添加、修改或删除数据的操作，但是不推荐如此操作，但是存在两个问题：
	- 安全性问题，用户的敏感信息会拼凑到Get请求行里，会显示到浏览器URL链接里。
	- 请求行有字符长短限制，文件过大时放不下。
	
###GET和POST的区别

1. GET提交的数据会放在URL之后，以?分割URL和传输数据，参数之间以&相连，如EditPosts.aspx?name=test1&id=123456.  POST方法是把提交的数据放在Post请求的Body中.
2. GET提交的数据大小有限制（因为浏览器对URL的长度有限制），而POST方法提交的数据没有限制.
3. GET方式需要使用Request.QueryString来取得变量的值，而POST方式通过Request.Form来获取变量的值。
4. GET方式提交数据，会带来安全问题，比如一个登录页面，通过GET方式提交数据时，用户名和密码将出现在URL上，如果页面可以被缓存或者其他人可以访问这台机器，就可以从历史记录获得该用户的账号和密码.

[原文](http://www.jianshu.com/p/80e25cb1d81a)