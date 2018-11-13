---
title: dnmap
categories: Information Gathering
tags: [portscanning,information gathering,recon,dnmap,kali linux]
date: 2016-10-20 08:52:56
---
0x00 dnmap介绍
-------------

dnmap（distributed nmap）是一款基于nmap的分布式扫描工具，它能够用一个集群来对另外一个大型集群网络进行扫描。
dnmap采用的是客户端/服务器体系结构，服务端主要是用来分发任务和汇总扫描状态，客户端主要用来执行扫描任务和记录自身的扫描状态。
该工具主要用于你想一个大型集群网络进行扫描，你自己拥有一个集群（肉鸡）的资源或者你的小伙伴想帮你的情况。

工具来源： http://mateslab.weebly.com/dnmap-the-distributed-nmap.html

[dnmap主页][1] | [Kali dnmap Repo仓库][2]

 - 作者：www.mateslab.com.ar
 - 证书：GPLv3

0x01 dnmap_client功能
-----------------

dnmap_client - 分布式nmap框架（客户端）

```shell
root@kali:~# dnmap_client -h
+----------------------------------------------------------------------+
| dnmap Client Version 0.6                                             |
| This program is free software; you can redistribute it and/or modify |
| it under the terms of the GNU General Public License as published by |
| the Free Software Foundation; either version 2 of the License, or    |
| (at your option) any later version.                                  |
|                                                                      |
| Author: Garcia Sebastian, eldraco@gmail.com                          |
| www.mateslab.com.ar                                                  |
+----------------------------------------------------------------------+

用法: /usr/bin/dnmap_client <选项>
选项:
  -s, --server-ip        dnmap服务器的IP地址
  -p, --server-port      dnmap服务器的IP地址端口，默认46001
  -a, --alias            您的别名，以便我们可以信贷给您的帮助，可选
  -d, --debug            调试
  -m, --max-rate         强制命令nmap最多使用最大速率，当nmap下来时添加--max-rate参数很管用
```

0x02 dnmap_server功能
---------------------

dnmap_server - 分布式nmap框架（服务端）

```shell
root@kali:~# dnmap_server -h
+----------------------------------------------------------------------+
| dnmap_server Version 0.6                                             |
| This program is free software; you can redistribute it and/or modify |
| it under the terms of the GNU General Public License as published by |
| the Free Software Foundation; either version 2 of the License, or    |
| (at your option) any later version.                                  |
|                                                                      |
| Author: Garcia Sebastian, eldraco@gmail.com                          |
| www.mateslab.com.ar                                                  |
+----------------------------------------------------------------------+

用法: /usr/bin/dnmap_server <选项>
选项:
  -f, --nmap-commands        Nmap命令文件
  -p, --port                 监听连接的TCP端口
  -L, --log-file             日志文件，默认为/var/log/dnmap_server.conf
  -l, --log-level            日志记录级别，默认详细
  -v, --verbose_level        显示执行详细级别(1-5)，默认1，级别0表示无输出
  -t, --client-timeout       客服端超时时间
  -s, --sort                 用于对静态值进行排序的字段。 您可以选择：Alias, #Commands, UpTime, RunCmdXMin, AvrCmdXMin, Status
  -P, --pem-file             pem文件用于TLS连接，默认情况下，我们使用当前目录中的服务器提供的server.pem文件

dnmap_server使用'<nmap-commands-file-name> .dnmaptrace'文件知道它从读取nmap命令文件中继续的地方，如果你想重新开始，只需删除'<nmap-commands-file-name> .dnmaptrace'文件即可。
```

0x03 dnmap_client用法示例
-----------------

```shell
root@kali:~# echo "nmap -F 192.168.1.0/24 -v -n -oA sub1" >> dnmap.txt
root@kali:~# echo "nmap -F 192.168.0.0/24 -v -n -oA sub0" >> dnmap.txt
root@kali:~# dnmap_server -f dnmap.txt
+----------------------------------------------------------------------+
| dnmap_server Version 0.6                                             |
| This program is free software; you can redistribute it and/or modify |
| it under the terms of the GNU General Public License as published by |
| the Free Software Foundation; either version 2 of the License, or    |
| (at your option) any later version.                                  |
|                                                                      |
| Author: Garcia Sebastian, eldraco@gmail.com                          |
| www.mateslab.com.ar                                                  |
+----------------------------------------------------------------------+

=| MET:0:00:00.000544 | Amount of Online clients: 0 |=
```
0x04 dnmap_server用法示例

```shell
root@kali:~# dnmap_client -s 192.168.1.15 -a dnmap-client1
+----------------------------------------------------------------------+
| dnmap Client Version 0.6                                             |
| This program is free software; you can redistribute it and/or modify |
| it under the terms of the GNU General Public License as published by |
| the Free Software Foundation; either version 2 of the License, or    |
| (at your option) any later version.                                  |
|                                                                      |
| Author: Garcia Sebastian, eldraco@gmail.com                          |
| www.mateslab.com.ar                                                  |
+----------------------------------------------------------------------+

Client Started...
Nmap output files stored in 'nmap_output' directory...
Starting connection...
Client connected succesfully...
Waiting for more commands....
        Command Executed: nmap -F 192.168.1.0/24 -v -n -oA sub1
```

  [1]: http://sourceforge.net/projects/dnmap/
  [2]: http://git.kali.org/gitweb/?p=packages/dnmap.git;a=summary