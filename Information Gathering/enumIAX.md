---
title: enumIAX
categories: Information Gathering
tags: [voip,information gathering,recon,enumeration,enumiax,kali linux]
date: 2016-10-23 16:43:45
---
0x00 enumIAX介绍
-------------

enumIAX（enum Inter Asterisk eXchange）是一个Asterisk系统内部交换协议用户名b暴力枚举工具。 enumIAX可以以两种不同的模式进行顺序用户名猜测或字典攻击。

Asterisk是一款GPLv2协议下的开源电话应用平台。简单来说，Asterisk是一个服务器应用，能够完成发起电话呼叫、接受电话呼叫、对电话呼叫进行定制处理，更多参考[开源应用架构之asterisk][1]。

工具来源：http://enumiax.sourceforge.net/

[enumIAX主页][2] | [Kali enumIAX Repo仓库][3]

 - 作者：Dustin D. Trammell
 - 证书：GPLv2

0x01 enumIAX功能
---------------

```shell
root@kali:~# enumiax -h
enumIAX 0.4a
Dustin D. Trammell <dtrammell@tippingpoint.com>

用法: enumiax [选项] 目标
  选项:
     -d <dict>  使用<dict>文件的字典攻击
     -i <count> 自动保存的间隔（操作数，默认1000）
     -m #       最小用户名长度（以字符为单位）
     -M #       最大用户名长度（以字符为单位）
     -r #       速率限制呼叫（以微秒为单位）
     -s <file>  从状态文件读取会话状态
     -v         增加详细程度（用于更多信息显示）
     -V         打印版本信息并退出
     -h         打印帮助/使用信息并退出
```

0x02 enumIAX用法示例
-----------------

```shell
root@kali:~# enumiax -d /usr/share/wordlists/metasploit/unix_users.txt 192.168.1.1
```

  [1]: http://blog.chinaunix.net/uid-7947787-id-3194117.html
  [2]: http://enumiax.sourceforge.net/
  [3]: http://git.kali.org/gitweb/?p=packages/enumiax.git;a=summary