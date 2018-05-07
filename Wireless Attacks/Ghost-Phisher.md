---
title: Ghost Phisher
categories: Wireless Attacks
tags: [kali linux,wireless attacks,information gathering,ghost phisher]
date: 2016-10-25 11:50:00
---
0x00 Ghost Phisher介绍
-------------

Ghost Phisher是一个使用Python编程语言和Python Qt GUI库编写的无线和以太网安全审计和攻击程序，可以伪造DNS服务器、DHCP服务器、HTTP服务器并且内置自动抓取和记录认证信息的功能模块。这个程序可用于制作蜜罐，也可用于钓鱼（安全测试）的相关工作。

Ghost Phisher目前支持以下功能：
```plain
HTTP服务器
内置RFC 1035 DNS服务器
内置RFC 2131 DHCP服务器
网页托管和凭证记录器（网络钓鱼）
Wifi接入点模拟器
会话劫持（被动和以太网模式）
ARP缓存欺骗（用于MITM和DOS攻击）
使用绑定的Metasploit进行渗透
使用SQlite数据库进行自动凭证日志记录
更新支持
```

工具来源：https://code.google.com/p/ghost-phisher/


[Ghost Phisher主页][1] | [Kali Ghost Phisher Repo仓库][2]

 - 作者：Saviour Emmanuel Ekiko

 - 证书：GPLv3



0x01 Ghost Phisher功能
---------------
ghost-phisher - 用于网络钓鱼和渗透攻击的图形用户界面套件


<!--more-->


0x02 Ghost Phisher用法示例
-----------------
YouTube：[How to create fake wifi hotspot (ghost phisher) using kali linux 2][3]
```shell
root@kali:~# ghost-phisher
```
![ghost-phisher.gif][4]


  [1]: https://code.google.com/p/ghost-phisher/
  [2]: http://git.kali.org/gitweb/?p=packages/ghost-phisher.git;a=summary
  [3]: https://www.youtube.com/watch?v=QpMZXp1NryE
  [4]: https://www.hackfun.org/usr/uploads/2016/10/690577029.gif