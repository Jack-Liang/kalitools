---
title: fragrouter
categories: Information Gathering
tags: [fragrouter,evasion,kali linux,recon,information gathering]
date: 2016-10-25 01:00:00
---
0x00 fragrouter介绍
-------------

fragrouter是一个具有路由器功能的应用程序，它能够对攻击者发送的攻击流量进行分片处理之后，向攻击目标转发。 

工具来源：fragrouter README


[fragrouter主页][1] | [Kali fragrouter Repo仓库][2]

 - 作者：Dug Song, Anzen Computing

 - 证书：GPLv2



0x01 fragrouter功能
---------------

fragrouter - 入侵检测系统(IDS)逃避工具包

```shell
root@kali:~# fragrouter
版本：1.6
用法：fragrouter [-i interface] [-p] [-g hop] [-G hopcount] ATTACK

其中ATTACK是以下之一：

-B1：base-1：正常的IP转发
-F1：frag-1：有序的8字节IP分片
-F2：frag-2：有序的24字节IP分片
-F3：frag-3：有序的8字节IP分片，一个失序
-F4：frag-4：有序的8字节IP分片，一个重复
-F5：frag-5：无序的8字节片段，一个重复
-F6：frag-6：有序的8字节片段，标记最后一个Frag
-F7：frag-7：有序的16字节片段，fwd重写
-T1：tcp-1：3-whs，错误TCP校验和和FIN/RST，有序的1字节段
-T3：tcp-3：3-whs，有序的1字节段，一个重复
-T4：tcp-4：3-whs，有序的1字节段，一次重写
-T5：tcp-5：3-whs，有序的2字节段，fwd重写
-T7：tcp-7：3-whs，有序的1字节段，交织空段
-T8：tcp-8：3-whs，有序的1字节段，一个失序
-T9：tcp-9：3-whs，无序的1字节段
-C2：tcbc-2：3-whs，有序的1字节段，交织的SYN
-C3：tcbc-3：有序的1字节空段，3-whs，有序的1字节段
-R1：tcbt-1：3-whs，RST，3-whs，有序的1字节段
-I2：ins-2：3-whs，有序的1字节段，错误TCP校验和
-I3：ins-3：3-whs，有序的1字节段，不设置ACK
-M1：misc-1：Windows NT 4 SP2 - http://www.dataprotect.com/ntfrag/
-M2：misc-2：Linux IP chain - http://www.dataprotect.com/ipchains/
```

0x02 fragrouter用法示例
-----------------

```shell
root@kali:~# fragrouter -i eth0 -F1
fragrouter: frag-1: ordered 8-byte IP fragments
...
```


  [1]: http://www.anzen.com/research/nidsbench/fragrouter.html
  [2]: http://git.kali.org/gitweb/?p=packages/fragrouter.git;a=summary