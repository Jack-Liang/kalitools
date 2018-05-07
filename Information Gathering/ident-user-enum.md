---
title: ident-user-enum
categories: Information Gathering
tags: [infogathering,ident-user-enum,recon,portscanning,information gathering,kali linux,enumeration]
date: 2017-04-23 08:22:00
---
0x00 介绍
-------
视频介绍：[https://asciinema.org/a/107704][1]
ident-user-enum是一个简单的PERL脚本，用于查询识别服务（113/TCP），以确定在目标系统的每个TCP端口上侦听进程的所有者。 这可以帮助在一个最好的时间内确定目标服务的优先级（您可能希望攻击以root用户身份运行的服务）。或者，所收集的用户名的列表可用于对其他网络服务的密码猜测攻击。

<!--more-->

工具来源：http://pentestmonkey.net/tools/user-enumeration/ident-user-enum
[主页][2] | [仓库][3]

 - 作者：pentestmonkey
 - 证书：MIT

0x01 功能
-------
```plain
root@kali:~# ident-user-enum
ident-user-enum v1.0 ( http://pentestmonkey.net/tools/ident-user-enum )

用法: ident-user-enum.pl ip地址 端口

查询识别（113 / TCP）以确定操作系统级用户运行该进程在给定的TCP端口上侦听服务。可以提供多个端口。
```
0x02 示例
-------
扫描远程主机（192.168.1.13），确定哪个用户在指定端口上运行服务（22 139 445）。
```plain
root@kali:~# ident-user-enum 192.168.1.13 22 139 445
ident-user-enum v1.0 ( http://pentestmonkey.net/tools/ident-user-enum )

192.168.1.13:22     root
192.168.1.13:139    root
192.168.1.13:445    root
```


  [1]: https://asciinema.org/a/107704
  [2]: http://pentestmonkey.net/tools/user-enumeration/ident-user-enum
  [3]: http://git.kali.org/gitweb/?p=packages/ident-user-enum.git