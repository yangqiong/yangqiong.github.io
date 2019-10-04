---
title: 套接字socket
date: 2019-10-05 07:43
tags: Linux, 计算机网络
---



## 套接字产生过程

```c
int socket(int family, int type, int protocal);
```

成功时返回一个小的非负整数值，与文件描述符类似，称之为**套接字描述符**。

为了得到这个套接字描述符，指定了协议簇，套接字类型，但是没有指定 *本地协议地址* 和 *远程协议地址* 。



```c
int bind(int sockfd, const struct sockaddr *myaddr, socklen_t addrlen);
```

bind函数把一个 *本地的协议地址* 赋予给了socket产生的套接字。



```C
int listen(int sockfd, int backlog);
```

内核为每一个**监听套接字**维护了两个队列，未完成连接队列和已完成连接队列。

当客户端通过connect发起三次握手时，当收到客户端三次握手第一个分节的SYN时，在未完成连接队列中创建一个新项。当收到三次握手的第三个分节ACK时，该项从未完成连接队列移到已完成队列。



```c
int accept(int sockfd, struct sockaddr *cliaddr, socklen_t *addrlen)
```

当调用accept时，已完成连接队列的队头项返回给进程，由内核自动生成一个全新的描述符，代表与所返回客户的TCP连接，称为**已连接套接字描述符**。



总结：一个服务器通常仅仅创建一个监听描述符，它在服务器的生命期内一直存在。内核为每个服务器进程接受的客户连接创建一个已连接套接字（也就是说对于它的TCP三次握手过程已经完成）。当服务器完成对某个给定客户的服务时，相应的已连接套接字就被关闭。



## 参考

* UNIX网络编程 卷一 第四章