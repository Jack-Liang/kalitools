---
title: golismero
categories: Information Gathering
tags: [information gathering,golismero,kali linux]
date: 2017-04-23 05:07:00
---
0x00 golismero介绍
-------------

GoLismero是安全性测试的开源框架。它是目前面向网络的安全性，但它可以很容易地扩展到其他类型的扫描。


<!--more-->


该框架的最有趣的特点是：
```plain
 - 真正的跨平台独立性，经过Windows，Linux，* BSD和OS X平台测试。
 - 没有平台本地库依赖，纯Python编写的框架。
 - 与使用Python和其他脚本语言编写的其他框架相比，性能较好。
 - 简单易用。
 - 插件开发非常简单。
 - 该框架还收集并统一了众所周知的工具的结果：sqlmap，xsser，openvas，dnsrecon，theharvester
 - 标准集成：CWE，CVE和OWASP。
 - 专为集群部署而设计（尚不可用）。
```
工具来源：https://github.com/golismero/golismero

[golismero主页][1] | [Kali golismero仓库][2]

 - 作者：Daniel Garcia
 - 证书：GPLv2

0x01 golismero功能
----------------

golismero - Web应用程序映射器
```plain

root@kali:~# golismero -h

/----------------------------------------------\
| GoLismero 2.0.0b3 - The Web Knife            |
| Contact: golismero.project<@>gmail.com       |
|                                              |
| Daniel Garcia Garcia a.k.a cr0hn (@ggdaniel) |
| Mario Vilas (@Mario_Vilas)                   |
\----------------------------------------------/

用法: golismero.py 命令 [目标...] [--选项]

  SCAN:
    扫描给定的目标漏洞，可选导入来自其他工具的结果并撰写报告。 
    后面的参数可以是域名，IP地址或网页。

  PROFILES:
    显示可用的配置文件列表，此命令不带参数。

  PLUGINS:
    显示可用的插件列表，此命令不带参数。

  INFO:
    显示给定插件的详细信息，后面的参数是插件ID。
    你可以使用glob风格的通配符。

  REPORT:
    从较早的扫描中生成报告。
    此命令不带参数，使用-o参数指定输出文件。

  IMPORT:
    从其他工具导入结果，并可选择生成报告，但不要扫描目标。
    此命令不带参数,使用-i参数指定输入文件。

  DUMP:
    从早期扫描中转储为SQL格式数据库。
    此命令不带参数，使用-o参数指定输出文件。

  UPDATE:
    将GoLismero更新到最新版本，需要安装Git且添加PATH变量环境。
    此命令不带参数。

示例:

  扫描网站并在屏幕上显示结果：
    golismero.py scan http://www.example.com

  导入Nmap结果，扫描发现的所有主机并写入HTML报告： 
    golismero.py scan -i nmap_output.xml -o report.html

  导入OpenVAS结果并在屏幕上显示，但不要扫描任何内容： 
    golismero.py import -i openvas_output.xml

  显示所有可用配置文件列表：
    golismero.py profiles

  显示所有可用插件列表：
    golismero.py plugins

  显示所有有关蛮力插件信息：
    golismero.py info brute_*

  转储上一次扫描的数据库：
    golismero.py dump -db example.db -o dump.sql
```

0x02 golismero用法示例
-----------------
对输入文件（-i /root/port80.xml）中的目标运行漏洞扫描（扫描），将输出保存到文件（-o sub1-port80.html）：
```shell
root@kali:~# golismero scan -i /root/port80.xml -o sub1-port80.html
```

  [1]: https://github.com/golismero/golismero
  [2]: http://git.kali.org/gitweb/?p=packages/golismero.git;a=summary