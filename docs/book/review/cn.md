# OSDI 七层模型

![20220323204039](https://cdn.jsdelivr.net/gh/weijiew/pic/images/20220323204039.png)

物(物理层)联(链路层)网(网络层)淑(传输层)慧(会话层)适(表示层)用(应用层)。

![20220323204220](https://cdn.jsdelivr.net/gh/weijiew/pic/images/20220323204220.png)

OSI 是一个标准，但是并不符合实际，实现起来复杂。

# TCP/IP

TCP 是 OSI 的简化版。分为应用层，传输层，网络层，网络接口层。



# UDP 协议

无连接的传输层协议，因为无连接所以不可靠。功能简单，没有流量控制，没有拥塞控制。

头部只有八字节所以开销小，源端口，目的端口，长度和校验和。

* 长度为报文段的字节数加上头部的字节数。
* 校验和是针对报文整体，包含数据报部分和头部计算出来一个数值，保证数据在运输过程中不出错。

![](image/cn/1645001321881.png)

适用于实时场景，例如视频多媒体之类。

# TCP 协议是什么？

TCP 是面向连接的可靠传输协议。TCP 是点对点，UDP 是一对多的协议。

GBN 协议是针对第一个发送的数据报进行计时，然后将之后的所有数据报重传。

SR 协议是针对发送窗口中的所有数据报，哪个数据报超时就重传哪个。

## TCP 多少字节？最大传输单元？

最大传输单元（MTU） 1500 字节，IP 头部 20 字节，TCP 头部 20 字节，所以 TCP 的数据报最多 1460 字节。

https://www.ruanyifeng.com/blog/2017/06/tcp-protocol.html

## 流量控制和拥塞控制区别？

流量控制是指控制两点之间的流量传输速度，通过调整窗口尺寸来实现，属于局部。
而拥塞控制是根据整个网络的拥塞情况来调整数据传输，拥塞情况则用丢包，超时等信息来判断，属于全局。

## 拥塞控制流程？

慢开始，拥塞避免，快重传，快恢复。

慢开始：拥塞窗口指数增长到设置的值。

快重传是指当收到连续三个连续的重复确认就重传，而不是等待超时再重传。

![](image/cn/1645282587821.png)

## 什么是累计确认？

例如接收端收到了 1，2，3，4，5 而发送端收到了 3 的确认，发送端就不用再逐个确认 1，2 了。收到 3 表示 3 之前的都已经收到了。

# Cookie 和 Session 的区别？

HTTP 是一种不保存状态，即无状态（stateless）协议。

HTTP 是无状态协议，Session 解决了这个问题。具体流程是在服务端针对用户创建相应的 Session 。但是客户端如何定位服务端相应用户的 Session ？主要是通过存储在客户端的 Cookie 中添加 Session id ，然后发送到服务端定位到相应的 Session 。

Cookie 和 Session 都是用来跟踪浏览器用户身份的会话方式，但是两者的应用场景不太一样。

Cookie 一般用来保存用户信息。Session 的主要作用就是通过服务端记录用户的状态。

Cookie 数据保存在客户端(浏览器端)，Session 数据保存在服务器端。相对来说 Session 安全性更高。

