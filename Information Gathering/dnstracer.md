---
title: dnstracer
categories: Information Gathering
tags: [dns,kali linux,dnstracer,information gathering,recon]
date: 2016-10-21 09:37:00
---
0x00 dnstracer介绍
-------------

dnstracer用于获取给定主机名从给定域名服务器（DNS）的信息，并跟随DNS服务器链得到权威结果。

工具来源：http://www.mavetju.org/unix/general.php

[dnstracer主页][1] | [Kali dnstracer Repo仓库][2]

 - 作者：Edwin Groothuis
 - 证书：BSD

0x01 dnstracer功能
---------------
dnstracer - 跟踪到源的DNS查询工具
```shell
root@kali:~# dnstracer 
DNSTRACER version 1.8.1 - (c) Edwin Groothuis - http://www.mavetju.org
用法: dnstracer [选项] [主机名]
	-c:                     禁用本地缓存,默认启用
	-C:                     启用负缓存，默认禁用
	-o:                     启用返回结果的概述，默认禁用
	-q <querytype>:         DNS请求查询类型，默认为A
	-r <retries>:           DNS请求的重试次数，默认值3
	-s <server>:            使用此服务器的初始请求，默认localhost，如果指定将使用A.ROOT-SERVERS.NET
	-t <maximum timeout>:   限制每次尝试等待的时间
	-v:                     显示详细
	-S <ip address>:        使用这个IP作为源地址
	-4:                     不查询IPv6服务器
```


<!--more-->


0x02 dnstracer用法示例
-----------------

```shell
root@kali:~# dnstracer -q mx -r 1 -t 10 -v www.harvard.edu
Tracing to www.harvard.edu[#mx] via 192.168.219.2, maximum of 1 retries
192.168.219.2 (192.168.219.2) IP HEADER
- Destination address:  192.168.219.2
DNS HEADER (send)
- Identifier:           0x351F
- Flags:                0x00 (Q )
- Opcode:               0 (Standard query)
- Return code:          0 (No error)
- Number questions:     1
- Number answer RR:     0
- Number authority RR:  0
- Number additional RR: 0
QUESTIONS (send)
- Queryname:            (3)www(7)harvard(3)edu
- Type:                 15 (unknown)
- Class:                1 (Internet)
DNS HEADER (recv)
- Identifier:           0x351F
- Flags:                0x8080 (R RA )
- Opcode:               0 (Standard query)
- Return code:          0 (No error)
- Number questions:     1
- Number answer RR:     1
- Number authority RR:  5
- Number additional RR: 4
QUESTIONS (recv)
- Queryname:            (3)www(7)harvard(3)edu
- Type:                 15 (unknown)
- Class:                1 (Internet)
ANSWER RR
- Domainname:           (3)www(7)harvard(3)edu
- Type:                 5 (CNAME)
- Class:                1 (Internet)
- TTL:                  5 (5s)
- Resource length:      36
- Resource data:        (3)www(7)harvard(3)edu(3)cdn(10)cloudflare(3)net
AUTHORITY RR
- Domainname:           (10)cloudflare(3)net
- Type:                 2 (NS)
- Class:                1 (Internet)
- TTL:                  5 (5s)
- Resource length:      6
- Resource data:        (3)ns3(10)cloudflare(3)net
AUTHORITY RR
- Domainname:           (10)cloudflare(3)net
- Type:                 2 (NS)
- Class:                1 (Internet)
- TTL:                  5 (5s)
- Resource length:      6
- Resource data:        (3)ns2(10)cloudflare(3)net
AUTHORITY RR
- Domainname:           (10)cloudflare(3)net
- Type:                 2 (NS)
- Class:                1 (Internet)
- TTL:                  5 (5s)
- Resource length:      6
- Resource data:        (3)ns1(10)cloudflare(3)net
AUTHORITY RR
- Domainname:           (10)cloudflare(3)net
- Type:                 2 (NS)
- Class:                1 (Internet)
- TTL:                  5 (5s)
- Resource length:      6
- Resource data:        (3)ns5(10)cloudflare(3)net
AUTHORITY RR
- Domainname:           (10)cloudflare(3)net
- Type:                 2 (NS)
- Class:                1 (Internet)
- TTL:                  5 (5s)
- Resource length:      6
- Resource data:        (3)ns4(10)cloudflare(3)net
ADDITIONAL RR
- Domainname:           (3)ns3(10)cloudflare(3)net
- Type:                 28 (unknown)
- Class:                1 (Internet)
- TTL:                  5 (5s)
- Resource length:      16
- Resource data:        2400:cb00:2049:0001:0000:0000:c629:de1f
ADDITIONAL RR
- Domainname:           (3)ns3(10)cloudflare(3)net
- Type:                 1 (A)
- Class:                1 (Internet)
- TTL:                  5 (5s)
- Resource length:      4
- Resource data:        198.41.222.31
ADDITIONAL RR
- Domainname:           (3)ns2(10)cloudflare(3)net
- Type:                 28 (unknown)
- Class:                1 (Internet)
- TTL:                  5 (5s)
- Resource length:      16
- Resource data:        2400:cb00:2049:0001:0000:0000:c629:de83
ADDITIONAL RR
- Domainname:           (3)ns2(10)cloudflare(3)net
- Type:                 1 (A)
- Class:                1 (Internet)
- TTL:                  5 (5s)
- Resource length:      4
- Resource data:        198.41.222.131
Got answer [received type is cname] 
 |\___ ns3.cloudflare.net [cloudflare.net] (2400:cb00:2049:0001:0000:0000:c629:de1f) IP HEADER
- Destination address:  XXX
DNS HEADER (send)
- Identifier:           0x303A
- Flags:                0x00 (Q )
- Opcode:               0 (Standard query)
- Return code:          0 (No error)
- Number questions:     1
- Number answer RR:     0
- Number authority RR:  0
- Number additional RR: 0
QUESTIONS (send)
- Queryname:            (3)www(7)harvard(3)edu
- Type:                 15 (unknown)
- Class:                1 (Internet)
send_data/sendto: Network is unreachable
```


  [1]: http://freshmeat.net/projects/dnstracer
  [2]: http://freshmeat.net/projects/dnstracer