---
title: Fierce
categories: Information Gathering
tags: [kali linux,fierce,information gathering,recon,dns]
date: 2016-10-24 11:05:00
---
0x00 Fierce介绍
-------------

首先Fierce不是一个IP扫描器，也不是一个DDoS工具，更不是设计为扫描整个互联网或执行任何非目标攻击的工具。 这意味着专门用于在公司网络内部和外部设定可能的目标。 仅列出这些目标（除非使用-nopattern开关），不执行任何利用（除非您使用-connect开关执行有意恶意的操作）。 Fierce是一种用于侦察的PERL脚本工具，它能使用几种策略快速扫描域（通常只需几分钟，在没有网络延迟的情况下）。

工具来源：http://ha.ckers.org/fierce/


[Fierce主页][1] | [Kali Fierce Repo仓库][2]

 - 作者：RSnake

 - 证书：GPLv2



0x01 Fierce功能
---------------

```shell
root@kali:~# fierce -h
fierce.pl (C) Copywrite 2006,2007 - By RSnake at http://ha.ckers.org/fierce/

    用法：perl fierce.pl [-dns example.com] [选项]

概述：
    Fierce是一种半轻量级扫描器，可帮助根据指定的域定位不连续的IP空间和主机名。确切的说是fierce扫描结果作为nmap，unicornscan，nessus，nikto等工具的输入，因为所有这些工具要求你已经知道你正在寻找什么IP空间。fierce不会不加区分地执行攻击和扫描整个互联网。这意味着它专门用于在公司网络内部和外部定位可能的目标。因为它主要使用DNS，你经常会发现因为错误地配置网络从而泄漏内部地址空间，这在定向恶意软件中特别有用。

选项：
    -connect    尝试用http方式连接到任何非RFC1918(公共)地址。这将输出返回headers信息，但请注意，对于一个有很多目 
                标的公司可能需要很长时间，取决于网络/机器的延迟，我不建议这样做，除非它是一个小公司或你有很多空闲时
                间（可能需要几个小时）。在指定的文件内，文本"Host:\n"将被指定的主机替换。用法：

    perl fierce.pl -dns example.com -connect headers.txt

    -delay       查找之间等待的秒数
    -dns         要扫描的域
    -dnsfile     使用文件中提供的DNS服务器（每行一个）进行反向查找（穷举模式）
    -dnsserver   使用特定的DNS服务器进行反向查找（可能应该是目标的DNS服务器），Fierce使用您的DNS服务器进行初始SOA                   
                 查询，然后默认情况下将目标的DNS服务器用于所有其他查询
    -file        您要输出以便记录到的文件
    -fulloutput  当与-connect结合使用时，将输出Web服务器发回的所有内容，而不仅仅是HTTP头
    -help        此屏幕的帮助信息
    -nopattern   在查找附近的主机时不要使用搜索模式，而是转储一切，这可能有点烦，但对于查找垃圾邮件制造者可能正在使   
                 用的其他域很有用，它也可能会给你很多误报，特别是扫描在大型域时
    -range       扫描内部IP范围（必须与-dnsserver组合）。注意，这不支持正则，只会简单地输出它找到的东西。用法：

    perl fierce.pl -range 111.222.333.0-255 -dnsserver ns1.example.com

   -search      搜索列表。当Fierce尝试遍历IP空间时，可能会遇到属于同一公司的其他域中的其他服务器。如果您为Fierce
                提供逗号分隔列表，它将报告找到的任何内容。如果公司服务器的名称与公众访问的网站不同时这将非常有用。  
                用法：

    perl fierce.pl -dns examplecompany.com -search corpcompany，blahcompany

               请注意，使用搜索还会大大扩展找到的主机数量，因为它会定位您在搜索列表中指定的服务器时继续遍历。所以越
               多越好
    -suppress  抑制所有TTY输出（与-file结合使用时）。
    -tcptimeout指定不同的超时（默认为10秒），如果您正在查询的DNS服务器速度较慢或有很多网络延迟，您可能需要增加此
               值。-threads指定扫描时使用的线程数（默认为单线程）
    -traverse  指定IP个数在根据你找到IP数，默认值为5以上
    -version   输出版本信息
    -wide      在找到C类中的任何匹配的主机名后，扫描整个C类地址，这将产生了更多的流量，但也可以发现更多的信息。
    -wordlist  使用单独的单词列表（每行一个单词）。用法：

    perl fierce.pl -dns examplecompany.com -wordlist dictionary.txt
```


<!--more-->


0x02 Fierce用法示例
-----------------

```shell
root@kali:~# fierce -dns harvard.edu -file /root/domains.txt
Now logging to /root/domains.txt
DNS Servers for harvard.edu:
	ext-dns-2.harvard.edu
	ext-dns-1.harvard.edu

Trying zone transfer first...
	Testing ext-dns-2.harvard.edu
		Request timed out or transfer not allowed.
	Testing ext-dns-1.harvard.edu
		Request timed out or transfer not allowed.

Unsuccessful in zone transfer (it was worth a shot)
Okay, trying the good old fashioned way... brute force

Checking for wildcard DNS...
Nope. Good.
Now performing 2280 test(s)...
128.103.149.62	ftscs.hul.harvard.edu
128.103.149.58	padly2.cadm.harvard.edu
128.103.149.53	idscs.hul.harvard.edu
128.103.149.48	krusty-149.soc.harvard.edu. 
128.103.149.45	hu-ldap-legacy.harvard.edu. 
128.103.149.42	icd3.isites.harvard.edu
128.103.149.37	cs2-public.cadm.harvard.edu. 
128.103.149.34	dbnode1.isites.harvard.edu. 
128.103.149.29	jump128-103-149.soc.harvard.edu. 
128.103.149.24	shstest.hres.harvard.edu
128.103.149.19	yardi60.hres.harvard.edu
...
...
```


  [1]: http://ha.ckers.org/fierce/
  [2]: http://git.kali.org/gitweb/?p=packages/fierce.git;a=summary