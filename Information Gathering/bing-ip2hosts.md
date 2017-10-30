---
title: bing-ip2hosts
categories: Information Gathering
tags: [enumeration,osint,information gathering,bing-ip2hosts,kali linux]
date: 2016-10-19 03:33:00
---
0x00 bing-ip2hosts介绍
-------------

Bing.com是微软拥有的以前称为MSN搜索和实时搜索的搜索引擎。它具有搜索在特定IP地址上的网站的独特功能。 Bing-ip2hosts使用此功能枚举Bing已为特定IP地址编入索引的所有主机名。这种技术被认为是在渗透测试的信息收集阶段的最佳方法，以便可以发现更大的潜在攻击面。 Bing-ip2hosts是用Linux上的Bash脚本语言编写的，因为使用移动接口的缘故，所以不需要API密钥。

工具来源：http://www.morningstarsecurity.com/research/bing-ip2hosts

[bing-ip2hosts主页][1] | [Kali bing-ip2hosts Repo仓库][2]

 - 作者：Andrew Horton
 - 证书：GPLv3

0x01 bing-ip2hosts功能
---------------

bing-ip2hosts - 使用bing.com枚举给定IP的主机名

```shell
root@kali:~# bing-ip2hosts -h
bing-ip2hosts (o.4) by Andrew Horton aka urbanadventurer
Homepage: http://www.morningstarsecurity.com/research/bing-ip2hosts

在渗透测试中的Web情报收集和攻击层面映射虚拟主机很有用
查找与目标共享IP地址的主机名，可以是主机名或IP地址
利用Microsoft Bing.com的能力通过IP地址搜索，例如：“IP：210.48.71.196”
用法: /usr/bin/bing-ip2hosts [选项] <IP地址|主机名>

选项:
-n       关闭进度指示动画
-t <DIR> 使用指定目录而不是/tmp目录，该目录必须存在
-i       可选CSV输出，在每行上输出IP和主机名，以逗号分隔
-p       可选http：//前缀输出，方便在shell中右键单击打开

```

0x02 bing-ip2hosts用法示例
-----------------

```shell
root@kali:~# bing-ip2hosts -p -t /root/test microsoft.com
[ 65.55.58.201 | Scraping 1 | Found 0 | / ]
http://microsoft.com
http://research.microsoft.com
http://www.answers.microsoft.com
http://www.microsoft.com
http://www.msdn.microsoft.com
```
```shell
root@kali:~# bing-ip2hosts -p -t /root/test 173.194.33.80
[ 173.194.33.80 | Scraping 60-69 of 73 | Found 41 | | ]| / ]
http://asia.google.com
http://desktop.google.com
http://ejabat.google.com
http://google.netscape.com
http://partner-client.google.com
http://picasa.google.com
```

0x03 提示
-------

最新的Kali已经移除了bing-ip2hosts，如果要使用bing-ip2hosts可以使用以下命令获取并安装：
```shell
root@kali:~# wget https://raw.githubusercontent.com/Strubbl/dotfiles/master/bin/bing-ip2hosts
root@kali:~# chmod +x bing-ip2hosts
root@kali:~# mv bing-ip2hosts /usr/bin/
```

  [1]: http://labs.portcullis.co.uk/application/acccheck
  [2]: http://git.kali.org/gitweb/?p=packages/acccheck.git;a=summary