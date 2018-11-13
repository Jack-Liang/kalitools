---
title: Amap
categories: Information Gathering
tags: [kali linux,amap,information gathering,amapcrap]
date: 2016-10-18 16:52:00
---
0x00 Amap介绍
===========

Amap是第首款针对渗透测试人员的下一代扫描工具， 它尝试识别即使在不同于正常端口的端口上运行应用程序。
Amap还可以通过发送触发数据包并在响应字符串列表中查找响应来识别基于非ascii编码的应用程序。

工具来源：https://www.thc.org/thc-amap/

[Amap主页][1] | [Kali Amap Repo仓库][2]

 - 作者：van Hauser and DJ RevMoon
 - 证书：其他

0x01 包含在Amap包的工具
================

amapcrap - 将随机数据发送到UDP，TCP或SSL端口以获取非法响应

```shell
root@kali:~# amapcrap 
amapcrap v5.4 (c) 2011 by van Hauser/THC <vh@thc.org>
语法：amapcrap [-S] [-u] [-m 0ab] [-M min，max] [-n connections] [-N delay] [-w delay] [-e] [-v] TARGET PORT 

选项： 
-S TCP连接后使用SSL（不能与 -u 同时使用） 
-u 使用UDP协议（默认值：TCP）（不能与 -c 同时使用） 
-n 连接最大连接数（默认值：无限制） 
-N 连接之间的延迟（ms）（默认值：0） 
-w 延迟关闭端口之前的延迟（默认值：250） 
-e 当服务器做出响应时不停止发送 
-v 详细模式 
-m 0ab 发送为随机垃圾数据：0-空字节，a-字母+空格，b-二进制 
-M min,max 随机垃圾数据的最小和最大长度 
TARGET PORT 发送随机垃圾数据的目标（ip或dns）和端口

此工具将随机数据发送到静默端口以获取非法响应以便下一步amap检测， 它输出适用于amap定义的形式。 
注意：默认情况下所有模式都将被激活（0：10%，a：40% b：50%），模式'a'总是发送以字母和空格结尾的行。 
可以访问我们的主页http://www.thc.org
```

amapcrap用法示例
------------

```shell
root@kali:~# amapcrap -n 20 -m a  192.168.1.15 80 -v
# Starting AmapCrap on 192.168.1.15 port 80
# Writing a "+" for every 10 connect attempts
# ++
done
```

amap – Application MAPper:渗透测试人员的下一代扫描工具

```shell
root@kali:~# amap
amap v5.4 (c) 2011 by van Hauser <vh@thc.org> www.thc.org/thc-amap
语法: amap [-A|-B|-P|-W] [-1buSRHUdqv] [[-m] -o <file>] [-D <file>] [-t/-T sec] [-c cons] [-C retries] [-p proto] [-i <file>] [target port [port] ...]
模式： 
-A 地图应用程序：发送触发包和分析响应（默认） 
-B 只抓取标识信息，不发送触发包
-P 不抓取标识信息横幅或应用程序的东西 - （全连接）端口扫描器 
选项： 
-1 只发送触发到端口，直到第一次标识。
-6 使用IPv6而不是IPv4 
-b 打印响应的ascii标识信息 
-i FILE 输出Nmap可读文件 
-u 在命令行上指定的端口UDP（默认为TCP） 
-R 不标识RPC服务 
-H 不发送被应用程序标记为潜在有害的触发包
-U 不要转储无法识别的响应（更脚本处理） 
-d 转储所有响应 
-v 详细模式，使用两次（或更多！）进行调试（不推荐:-) 
-q 不报告关闭的端口，并且不将其打印为不识别的 
-o FILE [-m] 将输出写入文件FILE，-m创建机器可读输出 
-c CONS 要进行的并行连接数（默认32，最大256） 
-C RETRIES 连接超时的重新连接数（请参见-T）（默认3） 
-T SEC 连接尝试的连接超时（以秒为单位）（默认为5） 
-t SEC 响应等待超时（以秒为单位）（默认值为5） 
-p PROTO 仅发送此协议的触发包（例如ftp） 
TARGET PORT 要扫描的目标地址和端口（除-i之外）
 
amap是用于标识目标端口上的应用程序协议的工具。 
注意：此版本不是使用SSL支持编译的！ 
使用提示：建议使用选项“-bqv”，“-1”快速检查。
```
Amap用法示例
-----------------

扫描192.168.1.15 80端口，显示接收的标识（b），不显示关闭端口（Q），并使用详细输出（V）：
```shell
root@kali:~# amap -bqv 192.168.1.15 21 
Using trigger file /etc/amap/appdefs.trig ... loaded 30 triggers
Using response file /etc/amap/appdefs.resp ... loaded 346 responses
Using trigger file /etc/amap/appdefs.rpc ... loaded 450 triggers

amap v5.4 (www.thc.org/thc-amap) started at 2016-10-18 14:24:02 - APPLICATION MAPPING mode

Total amount of tasks to perform in plain connect mode: 23
Waiting for timeout on 23 connections ...
Protocol on 192.168.1.15 :21/tcp matches ftp - banner: 220---------- Welcome to Pure-FTPd [privsep] ----------\r\n220-You are user number 7 of 5000 allowed.\r\n220-Local time is now 0224. Server port 21.\r\n220-This is a private system - No anonymous login\r\n220-IPv6 connections are also welcome on this ser
Protocol on 192.168.1.15 :21/tcp matches smtp - banner: 220---------- Welcome to Pure-FTPd [privsep] ----------\r\n220-You are user number 7 of 5000 allowed.\r\n220-Local time is now 0224. Server port 21.\r\n220-This is a private system - No anonymous login\r\n220-IPv6 connections are also welcome on this ser

amap v5.4 finished at 2016-10-18 14:24:02
```

```shell
root@kali:~# amap -bqv 192.168.1.15 80 
Using trigger file /etc/amap/appdefs.trig ... loaded 30 triggers
Using response file /etc/amap/appdefs.resp ... loaded 346 responses
Using trigger file /etc/amap/appdefs.rpc ... loaded 450 triggers

amap v5.4 (www.thc.org/thc-amap) started at 2016-10-18 14:25:57 - APPLICATION MAPPING mode

Total amount of tasks to perform in plain connect mode: 23
Waiting for timeout on 23 connections ...
Protocol on 192.168.1.15 :80/tcp matches http - banner: HTTP/1.1 400 Bad Request\r\nServer nginx\r\nDate Tue, 18 Oct 2016 182558 GMT\r\nContent-Type text/html\r\nContent-Length 166\r\nConnection close\r\n\r\n<html>\r\n<head><title>400 Bad Request</title></head>\r\n<body bgcolor="white">\r\n<center><h1>400 Bad

amap v5.4 finished at 2016-10-18 14:25:57
```


  [1]: http://www.thc.org/thc-amap/
  [2]: http://git.kali.org/gitweb/?p=packages/amap.git;a=summary