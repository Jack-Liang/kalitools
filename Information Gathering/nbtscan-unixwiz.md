---
title: nbtscan-unixwiz
categories: Information Gathering
tags: [nbtscan-unixwiz,information gathering,netbios,kali linux,recon,enumeration]
date: 2017-04-24 13:34:00
---
0x00 介绍
-------
一个在本地或远程TCP/IP网络上扫描开放的NETBIOS名称服务器的命令行工具。它基于Windows系统的nbtstat工具的功能实现，但它可在许多地址上运行，而不是仅一个地址。

<!--more-->

[主页][1] | [仓库][2]

 - 作者：Steve Friedl
 - 证书：public-domain

0x01 功能
-------

NBTSCAN-unixwiz - 开放NETBIOS名称服务器扫描器

```
root@kali:~# nbtscan-unixwiz
nbtscan 1.0.35 - 2008-04-08 - http://www.unixwiz.net/tools/

用法: nbtscan-unixwiz [选项] 目标 [目标...]

   目标可以是IP地址，DNS名称或地址的列表范围。
   范围可以表示成“192.168.12.0/24”或“192.168.12.64-97”

   -V        显示版本信息
   -f        显示完整的NBT资源记录响应(推荐)
   -H        生成HTTP请求头
   -v        开启详细输出调试
   -n        不查找响应IP地址的反向名称
   -p <n>    绑定UDP端口(默认0)
   -m        响应中包含MAC地址 (等同'-f')
   -T <n>    超时不响应 (默认2秒)
   -w <n>    次写入后等待秒数 (默认10ms)
   -t <n>    每个地址尝试次数(默认1次)
   -P        以perl的hashref格式生成结果
```
0x02 示例
-------
扫描一系列IP地址（192.168.0.100-110），而不进行反向名称查找（-n）：
```
root@kali:~# nbtscan-unixwiz -n 192.168.0.100-110
192.168.0.105   WORKGROUP\RETROPIE              SHARING
*timeout (normal end of scan)
```
扫描单个IP地址（192.168.0.38）并显示完整的NBT资源记录响应（-f）：
```
root@kali:~# nbtscan-unixwiz -f 192.168.0.38
192.168.0.38    WORKGROUP\DOOKOSSEL             SHARING
  DOOKOSSEL      <00> UNIQUE Workstation Service
  DOOKOSSEL      <03> UNIQUE Messenger Service<3>
  DOOKOSSEL      <20> UNIQUE File Server Service
  ..__MSBROWSE__.<01> GROUP  Master Browser
  WORKGROUP      <00> GROUP  Domain Name
  WORKGROUP      <1d> UNIQUE Master Browser
  WORKGROUP      <1e> GROUP  Browser Service Elections
  00:00:00:00:00:00   ETHER
```
视频演示：[https://asciinema.org/a/104243][3]


  [1]: http://unixwiz.net/tools/nbtscan.html
  [2]: http://git.kali.org/gitweb/?p=packages/nbtscan-unixwiz.git;a=tree;h=refs/heads/kali/master;hb=refs/heads/kali/master
  [3]: https://asciinema.org/a/104243