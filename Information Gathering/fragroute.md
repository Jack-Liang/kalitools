---
title: fragroute
categories: Information Gathering
tags: [kali linux,fragroute,information gathering,evasion]
date: 2016-10-24 14:40:23
---
0x00 fragroute介绍
-------------

Fragroute能够截取、修改和重写向外发送的报文，实现了大部分的IDS攻击功能。Fragroute起重要作用的是一个简单的规则设置语言，以它去实现延迟、复制、丢弃、碎片、重叠、打印、重排、分割、源路由或其他一些向目标主机发送数据包的攻击。这个工具开发的本意是去测试入侵检测系统、防火墙、基本的TCP/IP堆栈的行为。

该工具是为了帮助测试网络入侵检测系统，防火墙和基本TCP/IP堆栈行为而编写的，请不要滥用此软件！

工具来源：http://www.monkey.org/~dugsong/fragroute/

[fragroute主页][1] | [Kali fragroute Repo仓库][2]

 - 作者：Dug Song
 - 证书：3-Clause BSD

0x01 fragroute功能
---------------
fragroute - 通过尝试规避使用分段数据包来测试NIDS
```shell
root@kali:~# fragroute
Usage: fragroute [-f file] dst
Rules:
       delay first|last|random <ms>
       drop first|last|random <prob-%>
       dup first|last|random <prob-%>
       echo <string> ...
       ip_chaff dup|opt|<ttl>
       ip_frag <size> [old|new]
       ip_opt lsrr|ssrr <ptr> <ip-addr> ...
       ip_ttl <ttl>
       ip_tos <tos>
       order random|reverse
       print
       tcp_chaff cksum|null|paws|rexmit|seq|syn|<ttl>
       tcp_opt mss|wscale <size>
       tcp_seg <size> [old|new]
```

0x02 fragtest功能
---------------

fragtest - 通过尝试规避使用分段数据包来测试NIDS

```shell
root@kali:~# fragtest
用法: fragtest TESTS ... <host>
   其中TESTS是以下（或“全部”）的任意组合：

   ping         所有测试的先决条件
   ip-opt       确定支持的IP选项（BROKEN）
   ip-tracert   确定目标的路径
   frag         尝试8字节的IP分片
   frag-new     尝试8字节fwd重叠的IP分片，有利于新数据（BROKEN）
   frag-old     尝试8字节fwd重叠的IP分片，有利于旧数据
   frag-timeout 确定IP片段重组超时（BROKEN）
```

0x03 fragroute用法示例
-----------------

```shell
root@kali:~# fragroute 192.168.1.123
fragroute: tcp_seg -> ip_frag -> ip_chaff -> order -> print
172.16.79.182.53735 > 192.168.1.123.80: S 617662291:617662291(0) win 29200
```

0x05 fragtest用法示例
-----------------

```shell
root@kali:~# fragtest ip-tracert frag-new 192.168.1.123
ip-tracert: aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
```


  [1]: http://www.monkey.org/~dugsong/fragroute/
  [2]: http://git.kali.org/gitweb/?p=packages/fragroute.git;a=summary