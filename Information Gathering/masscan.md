---
title: masscan
categories: Information Gathering
tags: [masscan,portscanning,information gathering,kali linux,recon]
date: 2017-04-23 11:03:41
---
0x00 介绍
-------
视频介绍：[https://asciinema.org/a/31820][1]
masscan目前是最快的互联网端口扫描器，最快可以在六分钟内扫遍互联网。
masscan的扫描结果类似于nmap(一个很著名的端口扫描器)，在内部，它更像scanrand, unicornscan, and ZMap，采用了异步传输的方式。它和这些扫描器最主要的区别是，它比这些扫描器更快。而且，masscan更加灵活，它允许自定义任意的地址范和端口范围。
<!--more-->

[主页][2] | [仓库][3]

 - 作者：Robert Graham
 - 证书：GPLv2

0x01 功能
-------
masscan - 异步TCP端口扫描器
```plain
root@kali:~# masscan
用法:
masscan -p80,8000-8100 10.0.0.0/8 --rate=10000
 扫描一些Web端口10.x.x.x以每秒10000发包速率
masscan --nmap
 列出与nmap兼容的选项
masscan -p80 10.0.0.0/8 --banners -oB <filename>
 将二进制格式的扫描结果保存到<filename>
masscan --open --banners --readscan <filename> -oX <savefile>
 读取二进制扫描结果<filename>，并将其保存为xml格式<savefile>
```
0x02 更多参数
-------

```plain
<ip/range> IP地址范围，有三种有效格式：
1、单独的IPv4地址 
2、类似"10.0.0.1-10.0.0.233"的范围地址 
3、CIDR地址 类似于"0.0.0.0/0"，多个目标可以用都好隔开

-p <ports,--ports <ports>>         指定端口进行扫描

--banners                          获取banner信息，支持少量的协议

--rate <packets-per-second>        指定发包的速率

-c <filename>, --conf <filename>   读取配置文件进行扫描

--echo                             将当前的配置重定向到一个配置文件中

-e <ifname> , --adapter <ifname>   指定用来发包的网卡接口名称

--adapter-ip <ip-address>          指定发包的IP地址

--adapter-port <port>              指定发包的源端口

--adapter-mac <mac-address>        指定发包的源MAC地址

--router-mac <mac address>         指定网关的MAC地址

--exclude <ip/range>               IP地址范围黑名单，防止masscan扫描

--excludefile <filename>           指定IP地址范围黑名单文件

--includefile，-iL <filename>      读取一个范围列表进行扫描

--ping                             扫描应该包含ICMP回应请求

--append-output                    以附加的形式输出到文件

--iflist                           列出可用的网络接口，然后退出

--retries                          发送重试的次数，以1秒为间隔

--nmap                             打印与nmap兼容的相关信息

--http-user-agent <user-agent>     设置user-agent字段的值

--show [open,close]                告诉要显示的端口状态，默认是显示开放端口

--noshow [open,close]              禁用端口状态显示

--pcap <filename>                  将接收到的数据包以libpcap格式存储

--regress                          运行回归测试，测试扫描器是否正常运行

--ttl <num>                        指定传出数据包的TTL值，默认为255

--wait <seconds>                   指定发送完包之后的等待时间，默认为10秒

--offline                          没有实际的发包，主要用来测试开销

-sL                                不执行扫描，主要是生成一个随机地址列表

--readscan <binary-files>          读取从-oB生成的二进制文件，可以转化为XML或者JSON格式.

--connection-timeout <secs>        抓取banners时指定保持TCP连接的最大秒数，默认是30秒。
```

0x03 教程
-------
[Masscan：最快的互联网IP端口扫描器][4]
[Kali下masscan的使用][5]
[基于无状态的极速扫描技术][6]


  [1]: https://asciinema.org/a/31820
  [2]: https://github.com/robertdavidgraham/masscan
  [3]: http://git.kali.org/gitweb/?p=packages/masscan.git;a=summary
  [4]: http://www.freebuf.com/sectool/112583.html
  [5]: http://blog.csdn.net/isinstance/article/details/50466194
  [6]: http://www.91ri.org/10800.html