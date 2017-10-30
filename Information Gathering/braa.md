---
title: braa
categories: Information Gathering
tags: [kali linux,enumeration,braa,information gathering,snmp]
date: 2016-10-19 06:38:49
---
0x00 braa介绍
-------------

Braa是大规模SNMP扫描工具,这种工具的预期用途当然是使SNMP（Simple Network Management Protocol简单网络管理）查询 - 但不同于来自net-snmp的snmpget或snmpwalk，它能够在单个进程中同时查询几十或几百个主机。 因此，它消耗非常少的系统资源，并且扫描非常快。

Braa通过它的OWN snmp栈实现，所以它不需要任何SNMP库，如net-snmp。 它的实现非常脏，只支持几种数据类型，并且在任何情况下都不能说“符合标准”！ 但是它跑起来飞快， 因为这个原因（好吧，也是因为我的懒惰），在braa中没有ASN.1解析器 - 你必须知道OID的数值（例如.1.3.6.1.2.1.1.5.0 而不是用system.sysName.0）。

OID可以理解为有规则的设备参数编码，snmp协议将设备的各种参数按树形结构进行分组，从树的根部开始，每一个层级节点会有一个编码，将这些层级编码以“."作为分隔符，将其拼接起来所形成的一串编码就叫OID，通过OID可以对该OID表示的参数进行操作。
可以参考[SNMP监控一些常用OID的总结][1]

工具来源：braa README

[braa主页][2] | [Kali braaRepo仓库][3]

 - 作者：Mateusz ‘mteg’ Golicz
 - 证书：GPLv2

0x01 braa功能
---------------

Braa - 大规模SNMP扫描工具

```shell
root@kali:~# braa
braa 0.81 - Mateusz'mteg'Golicz <mtg@elsat.net.pl>，2003 - 2006
用法：braa [options] [query1] [query2] ...
  -h         显示此帮助
  -2         声明SNMP2C代理
  -v         执行所有查询后显示简要摘要
  -x         十六进制转储八位字节串
  -t <s>     获得响应前等待数秒
  -d <s>     发送每个数据包后等待微秒数
  -p <s>     在后续遍之间等待数毫秒
  -f <file>  从文件<file>加载查询（逐行）
  -a <time>  在<time>秒后退出
  -r <rc>    重试次数（默认值：3）

查询格式：
  GET:   [community@]iprange[:port]:oid[/id]
  WALK:  [community@]iprange[:port]:oid.*[/id]
  SET:   [community@]iprange[:port]:oid=value[/id]

例子：
         public@10.253.101.1:161:.1.3.6.*
         10.253.101.1-10.253.101.255:.1.3.6.1.2.1.1.4.0=sme
         10.253.101.1:.1.3.6.1.2.1.1.1.0/description

也可以一次指定多个查询：
         10.253.101.1-10.253.101.255:.1.3.6.1.2.1.1.4.0=sme,.1.3.6.*
         （将.1.3.6.1.2.1.1.4.0设置为'me'，并从.1.3.6开始）

SET查询的值必须在前面加上指定值类型的字符：
  i      是INTEGER类型
  a      是IPADDRESS类型
  s      是OCTET STRING类型
  o      是OBJECT IDENTIFIER类型
如果缺少类型说明符，则会自动检测值类型
```

0x02 braa用法示例
-----------------

使用公开公布的OID字符串在192.168.1.215上运行遍历SNMP树，查询.1.3.6下的所有OID：
```shell
root@kali:~# braa public@192.168.1.215:.1.3.6.*
192.168.1.215:122ms:.1.3.6.1.2.1.1.1.0:Linux redhat.biz.local 2.4.20-8 #1 Thu Mar 13 17:54:28 EST 2003 i686
192.168.1.215:143ms:.1.3.6.1.2.1.1.2.0:.1.3.6.1.4.1.8072.3.2.10
192.168.1.215:122ms:.1.3.6.1.2.1.1.3.0:4051218219
192.168.1.215:122ms:.1.3.6.1.2.1.1.4.0:Root <root@localhost> (configure /etc/snmp/snmp.local.conf)
192.168.1.215:143ms:.1.3.6.1.2.1.1.5.0:redhat.biz.local
```


  [1]: http://www.cnblogs.com/aspx-net/p/3554044.html
  [2]: http://s-tech.elsat.net.pl/
  [3]: http://git.kali.org/gitweb/?p=packages/braa.git;a=summary