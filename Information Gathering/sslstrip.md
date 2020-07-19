---
title: sslstrip
categories: Information Gathering
tags: [sslstrip, information gathering, kali linux]
date: 2020-07-19 08:57:45
---

介绍
------
sslstrip是一种工具，可以透明地劫持网络上的HTTP流量，监视HTTPS链接和重定向，然后将这些链接映射到外观相似的HTTP链接或与同形图相似的HTTPS链接。它还支持提供图标的模式，这些图标看起来像是锁定图标、选择性日志记录和会话拒绝。  

工具来源：https://github.com/moxie0/sslstrip  

[主页][1] | [仓库][2]  

+ 作者：Moxie Marlinspike
+ 证书：GPlv3  

sslstrip包中包含的工具
------

sslstrip – SSL/TLS中间人攻击工具  

```
root@kali:~# sslstrip -h

sslstrip 0.9 by Moxie Marlinspike
用法: sslstrip <options>

可选参数:
-w <filename>, --write=<filename> 指定要写入日志的文件（可选）。
-p , --post                       仅记录SSL POSTs（默认）。
-s , --ssl                        记录所有与服务器之间的SSL通信。
-a , --all                        记录所有与服务器之间的SSL和HTML通信。
-l <port>, --listen=<port>        要监听的端口（默认10000）。
-f , --favicon                    在安全请求上替换一个锁定图标。
-k , --killsessions               终止正在进行的会话。
-h                                显示此帮助信息。
```

sslstrip用法示例
------
将结果写入文件（-w sslstrip.log），监听8080端口（-l 8080）：
```
root@kali:~# sslstrip -w sslstrip.log -l 8080

sslstrip 0.9 by Moxie Marlinspike running...
```

  [1]: https://moxie.org/software/sslstrip/
  [2]: https://gitlab.com/kalilinux/packages/sslstrip
