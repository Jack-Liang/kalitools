---
title: lbd
categories: Information Gathering
tags: [kali linux,recon,lbd,information gathering,webapps]
date: 2017-04-23 09:46:00
---
0x00 介绍
-------
视频介绍：[https://asciinema.org/a/32257][1]
lbd(load balancing detector,负载平衡检测器)检测给定的域是否使用DNS/HTTP负载平衡（通过Server和DateHTTP响应头字段和服务器应答之间的差异）。

<!--more-->

[主页][2] | [仓库][3]

 - 作者：Stefan Behte
 - 证书：GPLv2

0x01 功能

-------
```plain
root@kali:~# lbd

lbd - load balancing detector 0.4 - Checks if a given domain uses load-balancing.
                                    Written by Stefan Behte (http://ge.mine.nu)
                                    Proof-of-concept! Might give false positives.
用法: /usr/bin/lbd [域名]

```
0x02 示例
-------
测试目标域（example.com）是否使用负载平衡：
```plain
root@kali:~# lbd example.com

lbd - load balancing detector 0.4 - Checks if a given domain uses load-balancing.
                                    Written by Stefan Behte (http://ge.mine.nu)
                                    Proof-of-concept! Might give false positives.

Checking for DNS-Loadbalancing: NOT FOUND
Checking for HTTP-Loadbalancing [Server]:
ECS (sea/55ED)
ECS (sea/1C15)
FOUND
```


  [1]: https://asciinema.org/a/32257
  [2]: http://ge.mine.nu/code/lbd
  [3]: http://git.kali.org/gitweb/?p=packages/lbd.git;a=summary