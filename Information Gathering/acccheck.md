---
title: acccheck
categories: Information Gathering
tags: [passwords,kali linux,acccheck,infogathering,password attack,smb,information gathering]
date: 2016-10-18 11:10:00
---
0x00 acccheck介绍
-------------

CDPSnarf（Cisco Discovery Protocol Sniffer）是专门用于从CDP包提取信息的网络嗅探器。 

工具来源：https://labs.portcullis.co.uk/tools/acccheck/

[acccheck主页][1] | [Kali acccheck仓库][2]

 - 作者：Faisal Dean
 - 证书：GPLv2

0x01 acccheck功能
---------------

acccheck-SMB的密码字典攻击工具

```shell
root@kali:~# acccheck

acccheck v0.2.1 - By Faiz

描述： 
根据给定的选择尝试连接到IPC $和ADMIN $共享，并尝试用户名和密码的组合，以望通过字典密码猜测攻击来识别给定帐户的密码

用法= ./acccheck [选项] 

-t [单个主机IP地址] 
或者
-T [包含目标IP地址的文件] 

选项： 
-p [单个密码] 
-P [包含密码的文件] 
-u [单用户] 
-U [包含用户名的文件] 
-v [详细模式] 

例子：
使用空密码尝试“管理员”帐户
acccheck -t 10.10.10.1 
尝试“password.txt”中所有密码穷举“管理员”帐户密码
acccheck -t 10.10.10.1 -P password.txt 
尝试“password.txt”中所有密码穷举“users.txt”中所有帐户密码
acccehck -t 10.10.10.1 -U users.txt -P password.txt 
针对单个用户尝试单个密码
acccheck -t 10.10.10.1 -u administrator -p password
```

0x02 acccheck用法示例
-----------------

扫描包含在SMB-ips.txt（T）的IP地址中使用空密码的默认账户Administrator，并使用详细输出（-v）：
```shell
root@kali:~# acccheck -T smb-ips.txt -v
Host:192.168.1.201, Username:Administrator, Password:BLANK
```


  [1]: http://labs.portcullis.co.uk/application/acccheck
  [2]: http://git.kali.org/gitweb/?p=packages/acccheck.git;a=summary