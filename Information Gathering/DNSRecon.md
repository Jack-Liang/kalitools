---
title: DNSRecon
categories: Information Gathering
tags: [kali linux,dnsrecon,information gathering,recon,dns]
date: 2016-10-21 06:00:00
---
0x00 DNSRecon介绍
-------------

DNSRecon提供一下功能：
```plain
检查域传送的所有NS记录
枚举给定域的一般DNS记录（MX，SOA，NS，A，AAAA，SPF和TXT）
执行常见的SRV记录枚举，顶级域名（TLD）扩展
支持通配符
蛮力穷举给定一个域和一个域名列表子域和主机A记录和AAAA记录
对给定的IP范围或CIDR执行PTR记录查找
检查DNS服务器A，AAAA和CNAME记录的缓存记录
枚举本地网络中的常见mDNS记录枚举主机并使用Google搜索子域
```

工具来源： DNSRecon README

[DNSRecon 主页][1] | [Kali DNSRecon Repo仓库][2]

 - 作者：Carlos Perez
 - 证书：GPLv2

[DNSRecon视频介绍][3]

0x01 DNSRecon功能
---------------

dnsrecon - 一个强大的DNS枚举脚本

```shell


选项:

-n, --name_server 
-D, --dictionary 
-f 过滤掉保存记录时解析为通配符定义的IP地址
root@kali:~# dnsrecon 
Version: 0.8.10
Usage: dnsrecon.py <options>

Options:
   -h, --help                   显示帮助信息并退出
   -d, --domain      <domain>   枚举的域目标
   -r, --range       <range>    用于蛮力穷举反向查找IP范围，形式可以为（开始IP-结束IP）或（范围/掩码）
   -n, --name_server <name>     要使用域服务器，如果没有给定将使用目标的SOA
   -D, --dictionary  <file>     用于蛮力穷举子域和主机名的字典文件。
   -f                           过滤掉穷举域查找结果，保存记录时解析到通配符定义的IP地址的记录
   -t, --type        <types>    枚举类型:
                                std       查询SOA，DNS，A，AAAA，MX和SRV记录（如果NS服务器的AXFR请求失败）
                                rvl       反向查找给定CIDR或IP范围
                                brt       使用给定字典文件蛮力穷举域名和主机
                                srv       SRV记录
                                axfr      测试所有NS服务器的域传送
                                goo       Google搜索子域和主机
                                snoop     对给定域的所有NS服务器执行缓存侦听，使用包含域的文件测试所有的服务器，                  使用-D选项提供文件
                                tld       删除给定域的TLD并针对在IANA中注册的所有TLD进行测试
                                zonewalk  使用NSEC记录执行DNSSEC域漫游
   -a                           执行AXFR进行标准枚举
   -s                           使用标准枚举对SPF记录中的IPv4范围执行反向查找。
   -g                           通过Google搜索执行标准的枚举
   -w                           在进行标准枚举时，通过Whois执行深度whois记录分析和反向查找IP范围
   -z                           使用标准枚举形式执行DNSSEC域漫游
   --threads         <number>   在反向查找，正向查找，强力和SRV记录枚举中使用的线程数
   --lifetime        <number>   等待服务器响应查询的时间
   --db              <file>     使用SQLite3文件格式保存找到的记录
   --xml             <file>     使用XML文件格式保存找到的记录
   --iw                         继续蛮力穷举域，即使发现通配符记录。
   -c, --csv         <file>     csv格式文件
   -j, --json        <file>     JSON格式文件
   -v                           在穷举模式中显示尝试详细
```


<!--more-->


0x02 DNSRecon用法示例
-----------------

```shell
root@kali:~# dnsrecon -d harvard.edu -D /usr/share/wordlists/dnsmap.txt  -t std -w --threads=10 --lifetime=20 --xml=test.xml -v
[*] Performing General Enumeration of Domain:
[-] DNSSEC is not configured for harvard.edu
[*] 	 SOA int-dns-2.harvard.edu 128.103.201.105
[*] 	 NS ext-dns-1.harvard.edu 128.103.200.35
[-] 	 Recursion enabled on NS Server 128.103.200.35
[*] 	 NS ext-dns-2.harvard.edu 128.103.200.162
[-] 	 Recursion enabled on NS Server 128.103.200.162
[*] 	 MX mx0b-00171101.pphosted.com 67.231.156.27
[*] 	 A harvard.edu 52.87.36.185
[*] 	 A harvard.edu 52.87.67.209
[*] Enumerating SRV Records
[*] 	 SRV _sip._tls.harvard.edu sipdir.online.lync.com 66.119.157.212 443 0
[*] 	 SRV _sip._tls.harvard.edu sipdir.online.lync.com 2603:1047:0:2::b 443 0
[*] 	 SRV _sipfederationtls._tcp.harvard.edu sipfed.online.lync.com 52.113.64.139 5061 0
[*] 	 SRV _sipfederationtls._tcp.harvard.edu sipfed.online.lync.com 2603:1047:0:2::b 5061 0
[*] 	 SRV _h323cs._tcp.harvard.edu vcsecluster01.noc.harvard.edu 128.103.247.202 1720 0
[*] 	 SRV _h323cs._tcp.harvard.edu vcsecluster01.noc.harvard.edu 128.103.247.201 1720 0
[*] 	 SRV _sip._udp.harvard.edu vcsecluster01.noc.harvard.edu no_ip 5060 0
[*] 	 SRV _sips._tcp.harvard.edu harvuni-expe01-sc1.uc.harvard.edu no_ip 5061 10
[*] 	 SRV _sips._tcp.harvard.edu harvuni-expe01-bv1.uc.harvard.edu 63.69.76.6 5061 10
[*] 9 Records Found
[*] Performing Whois lookup against records found.
[*] The following IP Ranges where found:
[*] 	 0) 128.103.0.0-128.103.255.255 Harvard University
[*] 	 1) 67.231.144.0-67.231.159.255 Proofpoint, Inc.
[*] 	 2) 52.84.0.0-52.95.255.255 Amazon Technologies Inc.
[*] 	 3) 66.119.144.0-66.119.159.255 Microsoft Corporation
[*] 	 4) 52.96.0.0-52.115.255.255 Microsoft Corporation
[*] 	 5) 63.69.76.0-63.69.77.255 Logistics Management Institute
[*] What Range do you wish to do a Revers Lookup for?
[*] number, comma separated list, a for all or n for none
0
[*] Harvard University
[*] Performing Reverse Lookup of range 128.103.0.0-128.103.255.255
[*] Performing Reverse Lookup from 128.103.0.0 to 128.103.255.255
[*] 	 PTR lmagw1-te-7-3-core.nox.org 128.103.0.74
[*] 	 PTR int-dns-3.harvard.edu 128.103.1.5
[*] 	 PTR endrun2-10wa.noc.harvard.edu 128.103.1.6
[*] 	 PTR time.harvard.edu 128.103.1.6
[*] 	 PTR internaldns-b3-n2.harvard.edu 128.103.1.10
[*] 	 PTR internaldns-b3-n2-ha.harvard.edu 128.103.1.11
[*] 	 PTR int-dns-3-node1.harvard.edu 128.103.1.12
[*] 	 PTR int-dns-3-node1-ha.harvard.edu 128.103.1.13
[*] 	 PTR int-dns-3-node2.harvard.edu 128.103.1.14
[*] 	 PTR vpn.noc.harvard.edu 128.103.1.20
[*] 	 PTR vpn5.harvard.edu 128.103.1.20
[*] 	 PTR time.harvard.edu 128.103.1.35
[*] 	 PTR endrun3-10wa.noc.harvard.edu 128.103.1.35
[*] 	 PTR netopc.harvard.edu 128.103.1.37
[*] 	 PTR registration.noc.harvard.edu 128.103.1.38
[*] 	 PTR registration-10wa.noc.harvard.edu 128.103.1.38
[*] 	 PTR usedby-reg10wa.noc.harvard.edu 128.103.1.39
[*] 	 PTR new-netopc.harvard.edu 128.103.1.40
[*] 	 PTR test.noc.harvard.edu 128.103.1.42
[*] 	 PTR sms.noc.harvard.edu 128.103.1.44
[*] 	 PTR autoregdev1-10wa.noc.harvard.edu 128.103.1.45
[*] 	 PTR portaldb2.noc.harvard.edu 128.103.1.46
[*] 	 PTR ext2-10wa.noc.harvard.edu 128.103.1.48
[*] 	 PTR portaldb1-10wa.noc.harvard.edu 128.103.1.51
[*] 	 PTR jnc-10wa.noc.harvard.edu 128.103.1.56
[*] 	 PTR rest-dev.noc.harvard.edu 128.103.1.61
[*] 	 PTR cdn-war10.noc.harvard.edu 128.103.1.133
[*] 	 PTR int-dns-3-node1-mgmt.harvard.edu 128.103.1.178
[*] 	 PTR int-dns-3-node2-mgmt.harvard.edu 128.103.1.179
[*] 	 PTR int-dns-1-node2-mgmt.harvard.edu 128.103.1.195
[*] 	 PTR dhcp-1.harvard.edu 128.103.1.210
[*] 	 PTR dhcp-1-node1.harvard.edu 128.103.1.211
[*] 	 PTR dhcp-1-node1-ha.harvard.edu 128.103.1.212
[*] 	 PTR dhcp-1-node2.harvard.edu 128.103.1.213
[*] 	 PTR dhcp-2.harvard.edu 128.103.1.242
[*] 	 PTR dhcp-2-node1.harvard.edu 128.103.1.243
[*] 	 PTR dhcp-2-node1-ha.harvard.edu 128.103.1.244
[*] 	 PTR dhcp-2-node2.harvard.edu 128.103.1.245
[*] 	 PTR dhcp-2-node2-ha.harvard.edu 128.103.1.246
[*] 	 PTR perdita.harvard.edu 128.103.4.2
[*] 	 PTR iceberg.harvard.edu 128.103.4.3
[*] 	 PTR camelot.harvard.edu 128.103.4.4
[*] 	 PTR paradise.harvard.edu 128.103.4.7
[*] 	 PTR intrigue.harvard.edu 128.103.4.8
[*] 	 PTR mikado.harvard.edu 128.103.4.9
[*] 	 PTR olympiad.harvard.edu 128.103.4.10
[*] 	 PTR tempo.harvard.edu 128.103.4.12
[*] 	 PTR peace.harvard.edu 128.103.4.11
[*] 	 PTR tuscany.harvard.edu 128.103.4.16
[*] 	 PTR troika.harvard.edu 128.103.4.21
[*] 	 PTR pilgrim.harvard.edu 128.103.4.23
[*] 	 PTR broadway.harvard.edu 128.103.4.24
[*] 	 PTR gypsy.harvard.edu 128.103.4.25
[*] 	 PTR winnie2.harvard.edu 128.103.4.26
[*] 	 PTR altissimo.harvard.edu 128.103.4.31
[*] 	 PTR pleasure.harvard.edu 128.103.4.32
[*] 	 PTR tamora.harvard.edu 128.103.4.33
[*] 	 PTR prince.harvard.edu 128.103.4.35
[*] 	 PTR polka.harvard.edu 128.103.4.36
[*] 	 PTR blaze.harvard.edu 128.103.4.37
[*] 	 PTR electron.harvard.edu 128.103.4.40
[*] 	 PTR winnie.harvard.edu 128.103.4.42
[*] 	 PTR lady-x.harvard.edu 128.103.4.43
[*] 	 PTR bologna.harvard.edu 128.103.4.44
[*] 	 PTR corylus.harvard.edu 128.103.4.45
[*] 	 PTR rugosa.harvard.edu 128.103.4.47
[*] 	 PTR tabriz.harvard.edu 128.103.4.48
[*] 	 PTR hansa.harvard.edu 128.103.4.49
[*] 	 PTR mundi.harvard.edu 128.103.4.50
[*] 	 PTR dhcp-0155095169-85-a1.client.fas.harvard.edu 128.103.4.67
[*] 	 PTR geophysics.harvard.edu 128.103.5.5
[*] 	 PTR itis-cmnsvc1.cadm.harvard.edu 128.103.6.5
[*] 	 PTR itis-cmnsvc2.cadm.harvard.edu 128.103.6.6
[*] 	 PTR stage-cdn-ox60.noc.harvard.edu 128.103.6.229
...
...一直在探测，十分钟后
...
[*] 	 PTR uhsmtafw1.net.harvard.edu 128.103.252.18
[*] 	 PTR arngw1.harvard.edu 128.103.252.46
[*] 	 PTR hrca-hrcagw-ser3.harvard.edu 128.103.252.50
[*] 	 PTR chs-nat1.harvard.edu 128.103.252.52
[*] 	 PTR hrca-hrcagw-ser6.harvard.edu 128.103.252.53
[*] 	 PTR hrca-orcvegw-ser1.harvard.edu 128.103.252.54
[*] 	 PTR chs-nat4.harvard.edu 128.103.252.55
[*] 	 PTR sergw1.harvard.edu 128.103.252.58
[*] 	 PTR meeigw1.harvard.edu 128.103.252.68
[*] 	 PTR vpn.hks.harvard.edu 128.103.252.68
[*] 	 PTR cfagw1.harvard.edu 128.103.252.90
[*] 	 PTR hbspgw1.harvard.edu 128.103.252.106
[*] 	 PTR harvard-rec-pcitest.fas.harvard.edu 128.103.252.128
[*] 	 PTR webvpn.hks.harvard.edu 128.103.252.155
[*] 	 PTR idmlbvip-stage.huit.harvard.edu 128.103.252.180
[*] 	 PTR idmlbvip-prod.huit.harvard.edu 128.103.252.181
[*] 	 PTR lock.hks.harvard.edu 128.103.253.5
[*] 	 PTR netapp2.hks.harvard.edu 128.103.253.6
[*] 	 PTR netapp.hks.harvard.edu 128.103.253.7
[*] 	 PTR p-papercut-dc1.hks.harvard.edu 128.103.253.9
[*] 	 PTR ppc.hks.harvard.edu 128.103.253.9
[*] 	 PTR hermia1.hks.harvard.edu 128.103.253.12
[*] 	 PTR hermia2.hks.harvard.edu 128.103.253.13
[*] 	 PTR eecrmapp.hks.harvard.edu 128.103.253.16
[*] 	 PTR fabian.hks.harvard.edu 128.103.253.19
[*] 	 PTR outbound1.hks.harvard.edu 128.103.253.20
[*] 	 PTR outbound2.hks.harvard.edu 128.103.253.21
[*] 	 PTR wsus.hks.harvard.edu 128.103.253.26
[*] 	 PTR cvsearch.hks.harvard.edu 128.103.253.28
[*] 	 PTR exed.hks.harvard.edu 128.103.253.37
[*] 	 PTR fta.hks.harvard.edu 128.103.253.38
[*] 	 PTR budget.hks.harvard.edu 128.103.253.40
[*] 	 PTR appmail.hks.harvard.edu 128.103.253.40
[*] 	 PTR mfe1.hks.harvard.edu 128.103.253.43
[*] 	 PTR quince.hks.harvard.edu 128.103.253.47
[*] 	 PTR smtp.hks.harvard.edu 128.103.253.49
[*] 	 PTR imappop.hks.harvard.edu 128.103.253.49
[*] 	 PTR apps.hks.harvard.edu 128.103.253.50
[*] 	 PTR web.hks.harvard.edu 128.103.253.50
[*] 	 PTR mail.hks.harvard.edu 128.103.253.51
[*] 	 PTR legacy.hks.harvard.edu 128.103.253.51
[*] 	 PTR mfeclg.hks.harvard.edu 128.103.253.51
[*] 	 PTR smtp.hks.harvard.edu 128.103.253.52
[*] 	 PTR p-kitefs-dc1.hks.harvard.edu 128.103.253.53
[*] 	 PTR case.hks.harvard.edu 128.103.253.54
[*] 	 PTR qa.cms.hks.harvard.edu 128.103.253.55
[*] 	 PTR admin.qa.www2.hks.harvard.edu 128.103.253.55
[*] 	 PTR eecrmiis.hks.harvard.edu 128.103.253.55
[*] 	 PTR ksgaccman.harvard.edu 128.103.253.56
[*] 	 PTR ksgsnoopy.hks.harvard.edu 128.103.253.56
[*] 	 PTR innovation.harvard.edu 128.103.253.56
[*] 	 PTR ksgexecprogram.harvard.edu 128.103.253.56
[*] 	 PTR zuckermanfellows.harvard.edu 128.103.253.56
[*] 	 PTR qa.www.hks.harvard.edu 128.103.253.56
[*] 	 PTR cid.harvard.edu 128.103.253.56
[*] 	 PTR hks.harvard.edu 128.103.253.56
[*] 	 PTR www.hks.harvard.edu 128.103.253.56
[*] 	 PTR www.exed.hks.harvard.edu 128.103.253.56
[*] 	 PTR www.democracy.ash.harvard.edu 128.103.253.56
[*] 	 PTR www.zuckermanfellows.harvard.edu 128.103.253.56
[*] 	 PTR www2.hks.harvard.edu 128.103.253.56
[*] 	 PTR ksglist.hks.harvard.edu 128.103.253.56
[*] 	 PTR ksgfiona.hks.harvard.edu 128.103.253.56
[*] 	 PTR ksgvideo.harvard.edu 128.103.253.56
[*] 	 PTR democracy.ash.harvard.edu 128.103.253.56
[*] 	 PTR yak.hks.harvard.edu 128.103.253.59
[*] 	 PTR casper.hks.harvard.edu 128.103.253.61
[*] 	 PTR autodiscover.hks17.harvard.edu 128.103.253.63
[*] 	 PTR autodiscover.hks18.harvard.edu 128.103.253.63
[*] 	 PTR mail.hks.harvard.edu 128.103.253.63
[*] 	 PTR autodiscover.hks.harvard.edu 128.103.253.63
[*] 	 PTR autodiscover.hks16.harvard.edu 128.103.253.63
[*] 17343 Records Found
[*] Saving records to XML file: test.xml

```

![dnsrecon.gif][4]


  [1]: https://github.com/darkoperator/dnsrecon
  [2]: http://git.kali.org/gitweb/?p=packages/dnsrecon.git;a=summary
  [3]: https://asciinema.org/a/31190
  [4]: https://www.hackfun.org/usr/uploads/2016/10/789991485.gif