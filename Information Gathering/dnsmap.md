---
title: dnsmap
categories: Information Gathering
tags: [information gathering,recon,dnsmap,dns,kali linux]
date: 2016-10-20 17:55:00
---
0x00 dnsmap介绍
-------------

dnsmap起源于2006年，是受到一个叫做“The Thief No One Saw”的小故事的启发后开发的，这个小故事能在Paul Craig的书《Stealing the Network - How to Own the Bow》中找到。
dnsmap 主要用来在渗透测试的信息收集阶段来协助测试网络的基础设施的安全性，它能发现目标的网段，域名，甚至是电话号码等等。
子域名穷举在穷举子域名方面也是一项新的技术，尤其是在域传送技术失效的时候。（在最近我很少看到公开允许域传输的例子)

工具来源：http://code.google.com/p/dnsmap/

[dnsmap主页][1] | [Kali dnsmap Repo仓库][2]

 - 作者：pagvac
 - 证书：GPLv2

0x01 dnsmap功能
---------------

dnsmap - DNS域名蛮力穷举工具

```shell
root@kali:~# dnsmap
dnsmap 0.30 - DNS Network Mapper by pagvac (gnucitizen.org)

用法: dnsmap <目标域> [选项]
选项:
-w <指定字典文件>
-r <指定结果以常规格式输出文件>
-c <指定结果以csv格式输出文件>
-d <设置延迟(毫秒)>
-i <忽略的IP> (当你遇到一个虚假的IP地址时很有用)

示例:
dnsmap target-domain.com
dnsmap target-domain.com -w yourwordlist.txt -r /tmp/domainbf_results.txt
dnsmap target-fomain.com -r /tmp/ -d 3000
dnsmap target-fomain.com -r ./domainbf_results.txt
```


<!--more-->


0x02 dnsmap用法示例
-----------------

```shell
root@kali:~# dnsmap example.com -w /usr/share/wordlists/dnsmap.txt
dnsmap 0.30 - DNS Network Mapper by pagvac (gnucitizen.org)

[+] searching (sub)domains for example.com using /usr/share/wordlists/dnsmap.txt
[+] using maximum random delay of 10 millisecond(s) between requests
```

0x02 dnsmap-bulk用法示例
--------------------

```shell
root@kali:~# dnsmap-bulk.sh domain.txt 
dnsmap 0.30 - DNS Network Mapper by pagvac (gnucitizen.org)

[+] searching (sub)domains for acm.cuit.edu.cn using built-in wordlist
[+] using maximum random delay of 10 millisecond(s) between requests

[+] 0 (sub)domains and 0 IP address(es) found
[+] completion time: 17 second(s)
dnsmap 0.30 - DNS Network Mapper by pagvac (gnucitizen.org)

[+] error: entered domain is not valid!
dnsmap 0.30 - DNS Network Mapper by pagvac (gnucitizen.org)

[+] error: entered domain is not valid!
dnsmap 0.30 - DNS Network Mapper by pagvac (gnucitizen.org)

[+] error: entered domain is not valid!
dnsmap 0.30 - DNS Network Mapper by pagvac (gnucitizen.org)

[+] searching (sub)domains for 210.41.225.250 using built-in wordlist
[+] using maximum random delay of 10 millisecond(s) between requests
...
...
```

  [1]: http://code.google.com/p/dnsmap/
  [2]: http://git.kali.org/gitweb/?p=packages/dnsmap.git;a=summary