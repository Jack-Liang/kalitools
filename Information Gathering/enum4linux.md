---
title: enum4linux
categories: Information Gathering
tags: [information gathering,recon,smb,enumeration,enum4linux,kali linux]
date: 2016-10-23 15:59:00
---
0x00 enum4linux介绍
-------------

enum.exe的Linux替代软件，用于枚举Windows和Samba主机中的数据。

概述：
```plain
Enum4linux是一个用于枚举来自Windows和Samba系统的信息的工具。 它试图提供与以前从www.bindview.com可用的enum.exe类似的功能。

它是用Perl编写的，基本上是一个包装Samba工具smbclient，rpclient，net和nmblookup。

工具的用法可以在下面找到例子，以前版本的工具可以在页面底部找到。

dnstracer用于获取给定主机名从给定域名服务器（DNS）的信息，并跟随DNS服务器链得到权威结果。
```
主要特性：
```plain
RID循环（当Windows 2000上的RestrictAnonymous设置为1时）
用户列表（当Windows 2000上的RestrictAnonymous设置为0时）
组成员信息列表
共享枚举
检测主机是否在工作组或域中
识别远程操作系统
密码策略检索（使用polenum）
```
工具来源：https://labs.portcullis.co.uk/tools/enum4linux/

[dnstracer主页][1] | [Kali dnstracer Repo仓库][2]

 - 作者：Mark Lowe

 - 证书：GPLv2



0x01 enum4linux功能
---------------

```shell
root@kali:~# enum4linux -h
enum4linux v0.8.9 (http://labs.portcullis.co.uk/application/enum4linux/)
Copyright (C) 2011 Mark Lowe (mrl@portcullis-security.com)

简单的封装了在samba包中的工具，以提供类似的enum.exe功能（以前从www.bindview.com）。 为了方便起见，还增加了一些附加功能，例如RID循环。

用法: ./enum4linux.pl [选项] ip地址

枚举选项：
     -U        获取用户列表
     -M        获取机器列表*
     -S        获取共享列表
     -P        获取密码策略信息
     -G        获取组和成员列表
     -d        详述适用于-U和-S
     -u user   用户指定要使用的用户名（默认""）
     -p pass   指定要使用的密码（默认为""）

以下选项是enum.exe未实现的: -L, -N, -D, -f

其他选项:
    -a        做所有简单枚举（-U -S -G -P -r -o -n -i），如果您没有提供任何其他选项，则启用此选项
    -h        显示此帮助消息并退出
    -r        通过RID循环枚举用户
    -R range  RID范围要枚举（默认值：500-550,1000-1050，隐含-r）
    -K n      继续搜索RID，直到n个连续的RID与用户名不对应，Impies RID范围结束于999999.对DC有用
    -l        通过LDAP 389 / TCP获取一些（有限的）信息（仅适用于DN）
    -s        文件暴力猜测共享名称
    -k user   远程系统上存在的用户（默认值：administrator，guest，krbtgt，domain admins，root，bin，none）
              用于获取sid与“lookupsid known_username”
              使用逗号尝试几个用户：“-k admin，user1，user2”
    -o        获取操作系统信息
    -i        获取打印机信息
    -w wrkg   手动指定工作组（通常自动找到）
    -n        做一个nmblookup（类似于nbtstat）
    -v        详细输出，显示正在运行的完整命令（net，rpcclient等）

RID循环应从Windows（或Samba）主机中提取一个用户列表，其中限制匿名设置为1（Windows NT和2000）或启用“网络访问：允许匿名SID /名称转换”（XP，2003）。

注意：Samba服务器通常似乎有RID在范围3000-3050。

依赖性信息：您将需要安装samba包，因为此脚本基本上只是一个包装rpcclient，net，nmblookup和smbclient。 Polenum从http://labs.portcullis.co.uk/application/polenum/需要获取密码政策信息。
```

0x02 enum4linux用法示例
-----------------

```shell
root@kali:~# enum4linux -a -o www.harvard.edu
Starting enum4linux v0.8.9 ( http://labs.portcullis.co.uk/application/enum4linux/ ) on Mon Oct 24 00:37:22 2016

 ========================== 
|    Target Information    |
 ========================== 
Target ........... www.harvard.edu
RID Range ........ 500-550,1000-1050
Username ......... ''
Password ......... ''
Known Usernames .. administrator, guest, krbtgt, domain admins, root, bin, none


 ======================================================= 
|    Enumerating Workgroup/Domain on www.harvard.edu    |
 ======================================================= 
[E] Can't find workgroup/domain


 =============================================== 
|    Nbtstat Information for www.harvard.edu    |
 =============================================== 
Looking up status of 104.16.155.6
No reply from 104.16.155.6

 ======================================== 
|    Session Check on www.harvard.edu    |
 ======================================== 
Use of uninitialized value $global_workgroup in concatenation (.) or string at ./enum4linux.pl line 437.
[E] Server doesn't allow session using username '', password ''.  Aborting remainder of tests.
```


  [1]: https://labs.portcullis.co.uk/tools/enum4linux/
  [2]: http://git.kali.org/gitweb/?p=packages/enum4linux.git;a=summary