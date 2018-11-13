---
title: intrace
categories: Information Gathering
tags: [information gathering,kali linux,intrace,evasion,recon]
date: 2017-04-23 08:54:45
---
0x00 介绍
-------
InTrace是一款类似于Traceroute的被动路由跟踪工具。但它不同的是，他不主动发送数据包，而是通过监听当前主机和目标主机的数据包，进行分析，从而获取路由信息。这样既可以进行网络侦查，又可以绕过防火墙的限制，避免被防火墙发现。工具使用非常简单，只要开启监听，然后等待获取和目标主机的数据包，然后就可以获取路由跟踪信息了。使用的时候需要指定端口。该端口号必须在TCP连接中使用到。否则，就无法捕获对应的数据包。

<!--more-->

[主页][1] | [仓库][2]

 - 作者：Robert Swiecki
 - 证书：GPLv3

0x01 功能
-------
```plain
root@kali:~# intrace
InTrace, version 1.5 (C)2007-2011 Robert Swiecki <robert@swiecki.net>
2014/05/20 09:59:29.627368 <INFO> 用法: intrace <-h 主机> [-p <端口>] [-d <调试级别>] [-s <载荷大小>] [-6]
```
0x02 示例
-------
使用数据包大小为4字节（-s 4），指定端口80（-p 80）向目标主机（-h www.example.com）进行路由跟踪：
```plain
root@kali:~# intrace -h www.example.com -p 80 -s 4
InTrace 1.5 -- R: 93.184.216.119/80 (80) L: 192.168.1.130/51654
Payload Size: 4 bytes, Seq: 0x0d6dbb02, Ack: 0x8605bff0
Status: Packets sent #8

  #  [src addr]         [icmp src addr]    [pkt type]
 1.  [192.168.1.1    ]  [93.184.216.119 ]  [ICMP_TIMXCEED]
 2.  [192.168.0.1    ]  [93.184.216.119 ]  [ICMP_TIMXCEED]
 3.  [  ---          ]  [  ---          ]  [NO REPLY]
 4.  [64.59.184.185  ]  [93.184.216.119 ]  [ICMP_TIMXCEED]
 5.  [66.163.70.25   ]  [93.184.216.119 ]  [ICMP_TIMXCEED]
 6.  [66.163.64.150  ]  [93.184.216.119 ]  [ICMP_TIMXCEED]
 7.  [66.163.75.117  ]  [93.184.216.119 ]  [ICMP_TIMXCEED]
 8.  [206.223.119.59 ]  [93.184.216.119 ]  [ICMP_TIMXCEED]
```

  [1]: http://code.google.com/p/intrace/
  [2]: http://git.kali.org/gitweb/?p=packages/intrace.git;a=summary