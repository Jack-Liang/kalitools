---
title: DMitry
categories: Information Gathering
tags: [information gathering,recon,dmitry,kali linux,portscanning]
date: 2016-10-20 08:19:00
---
0x00 DMitry介绍
-------------

DMitry(Deepmagic Information Gathering Tools 深度信息收集工具)是一个linux下用C语言写的工具。它能够尽可能的获取指定主机目标的信息。基础功能是获取目标的子域名，Email地址，运行时间相关信息，tcp端口，whois信息等等。

特性：

```plain
 - 软件开源
 - 可以同时进行一系列的whois查询
 - 获取运行时的数据，系统和服务器信息
 - 对指定的机器搜索获取其子域名
 - 在指定的主机上搜素Email
 - 对指定的主机搜索其开启的TCP端口
 - 有模块化系统可以让用户根据需要选择模块
```

工具来源：http://mor-pah.net/software/dmitry-deepmagic-information-gathering-tool/

[DMitry主页][1] | [Kali DMitry Repo仓库][2]

 - 作者：James Greig
 - 证书：GPLv3

[DMitry视频介绍][3]

0x01 DMitry功能
---------------

DMitry - 深度信息收集工具

```shell
root@kali:~# dmitry
Deepmagic Information Gathering Tool
"There be some deep magic going on"

用法：dmitry [-winsepfb] [-t 0-9] [-o %host.txt] host
-o        将输出保存到%host.txt或由-o文件指定的文件
-i        对主机的IP地址执行whois查找
-w        对主机的域名执行whois查找
-n        在Netcraft.com上检索主机信息
-s        搜索的子域
-e        搜索可能的电子邮件地址
-p        在主机上执行TCP端口扫描
* -f      在显示输出报告过滤端口的主机上执行TCP端口扫描
* -b      读取从扫描端口接收的横幅
* -t 0-9  设置扫描TCP端口时的TTL（默认值2）
* 以上3个选项需要传递-p选项
```

0x02 DMitry用法示例
-----------------

```shell
root@kali:~# dmitry -winsepo harvard.txt harvard.edu
Deepmagic Information Gathering Tool
"There be some deep magic going on"

Writing output to 'harvard.txt'

HostIP:52.87.36.185
HostName:harvard.edu

Gathered Inet-whois information for 52.87.36.185
---------------------------------


inetnum:        52.0.0.0 - 52.144.63.255
netname:        NON-RIPE-NCC-MANAGED-ADDRESS-BLOCK
descr:          IPv4 address block not managed by the RIPE NCC
remarks:        ------------------------------------------------------
remarks:
remarks:        You can find the whois server to query, or the
remarks:        IANA registry to query on this web page:
remarks:        http://www.iana.org/assignments/ipv4-address-space
remarks:
remarks:        You can access databases of other RIRs at:
remarks:
remarks:        AFRINIC (Africa)
remarks:        http://www.afrinic.net/ whois.afrinic.net
remarks:
remarks:        APNIC (Asia Pacific)
remarks:        http://www.apnic.net/ whois.apnic.net
remarks:
remarks:        ARIN (Northern America)
remarks:        http://www.arin.net/  whois.arin.net
remarks:
remarks:        LACNIC (Latin America and the Carribean)
remarks:        http://www.lacnic.net/ whois.lacnic.net
remarks:
remarks:        IANA IPV4 Recovered Address Space
remarks:        http://www.iana.org/assignments/ipv4-recovered-address-space/ipv4-recovered-address-space.xhtml
remarks:
remarks:        ------------------------------------------------------
country:        EU # Country is really world wide
admin-c:        IANA1-RIPE
tech-c:         IANA1-RIPE
status:         ALLOCATED UNSPECIFIED
mnt-by:         RIPE-NCC-HM-MNT
mnt-lower:      RIPE-NCC-HM-MNT
mnt-routes:     RIPE-NCC-RPSL-MNT
created:        2016-09-26T14:44:02Z
last-modified:  2016-09-26T14:44:02Z
source:         RIPE

role:           Internet Assigned Numbers Authority
address:        see http://www.iana.org.
admin-c:        IANA1-RIPE
tech-c:         IANA1-RIPE
nic-hdl:        IANA1-RIPE
remarks:        For more information on IANA services
remarks:        go to IANA web site at http://www.iana.org.
mnt-by:         RIPE-NCC-MNT
created:        1970-01-01T00:00:00Z
last-modified:  2001-09-22T09:31:27Z
source:         RIPE # Filtered

% This query was served by the RIPE Database Query Service version 1.87.4 (DB-1)



Gathered Inic-whois information for harvard.edu
---------------------------------

Domain Name: HARVARD.EDU

Registrant:
   Harvard University
   HUIT Network Services
   60 Oxford Street
   Cambridge, MA 02138
   UNITED STATES

Administrative Contact:
   Luke Sullivan
   Manager, Network Systems
   Harvard University
   60 Oxford Street
   Cambridge, MA 02138
   UNITED STATES
   (617) 384-6640
   luke_sullivan@harvard.edu

Technical Contact:
   Network Operations
   Harvard University
   HUIT Network Services
   60 Oxford Street
   Cambridge, MA 02138
   UNITED STATES
   (617) 495-7777
   netmanager@harvard.edu

Name Servers: 
   EXT-DNS-1.HARVARD.EDU      128.103.200.35
   EXT-DNS-2.HARVARD.EDU      128.103.200.162

Domain record activated:    27-Jun-1985
Domain record last updated: 30-Dec-2015
Domain expires:             31-Jul-2017



Gathered Netcraft information for harvard.edu
---------------------------------

Retrieving Netcraft.com information for harvard.edu
Netcraft.com Information gathered

Gathered Subdomain information for harvard.edu
---------------------------------
Searching Google.com:80...
Unable to connect: Socket Connect Error
```

  [1]: http://mor-pah.net/software/dmitry-deepmagic-information-gathering-tool/
  [2]: http://git.kali.org/gitweb/?p=packages/dmitry.git;a=summary
  [3]: https://asciinema.org/a/31154
