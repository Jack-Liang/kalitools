---
title: APT2
categories: Information Gathering
tags: [kali linux,APT2,information gathering,Penetration]
date: 2019-04-19 17:47:00
---

APT2 Package Description
========================

自动渗透测试工具包。

此工具将执行NMap扫描，或从Nexpose，Nessus或NMap导入扫描结果。 处理结果将用于根据可配置的安全级别和枚举服务信息启动漏洞利用和枚举模块。

所有模块结果都存储在localhost中，并且是APT2知识库（KB）的一部分。 可以从应用程序中访问KB，并允许用户查看漏洞利用模块的收集结果。

工具来源: https://github.com/MooseDojo/apt2

[主页][1] | [仓库][2]

作者：Adam Compton 、 Austin Lane

证书：MIT

APT2 帮助
=========

```
root@kali:~# apt2 -h

用法： apt2 [-h] [-C <config.txt>] [-f [<input file> [<input file> ...]]]
            [--target] [--ip <local IP>] [-v] [-s SAFE_LEVEL]
            [-x EXCLUDE_TYPES] [-b] [--listmodules]

可选参数：

  -h, --help            显示此帮助消息并退出
  -v, --verbosity       increase output verbosity
  -s SAFE_LEVEL, --safelevel SAFE_LEVEL
                        设置模块得最低安全级别。0表示不安全，5表示非常安全。
                        默认值为4。






```








  [1]: https://github.com/MooseDojo/apt2
  [2]: http://git.kali.org/gitweb/?p=packages/apt2.git
