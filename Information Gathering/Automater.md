---
title: Automater
categories: Information Gathering
tags: [information gathering,kali linux,automater]
date: 2016-10-19 02:31:51
---
0x00 Automater介绍
-------------

Automater是一个URL /域，IP地址和Md5哈希开源情报工具，旨在为入侵分析师使分析过程更容易。 给定一个目标（URL，IP或HASH）或一个完整的目标文件，Automater将返回来自如下来源的相关结果：IPvoid.com，Robtex.com，Fortiguard.com，unshorten.me，Urlvoid.com，Labs。 alienvault.com，ThreatExpert，VxVault和VirusTotal。

工具来源：http://www.tekdefense.com/automater/

[Automater主页][1] | [Kali AutomaterRepo仓库][2]

 - 作者：TekDefense.com
 - 证书：其他

0x01 Automater功能
---------------

automater - 一个IP和URL分析工具

```shell
root@kali:~# automater -h
用法：Automater.py [-h] [-o OUTPUT] [-b] [-f CEF] [-w WEB] [-c CSV]
                    [-d DELAY] [-s SOURCE] [--proxy PROXY] [-a USERAGENT] [-V]
                    [-r] [-v]
                    target

IP，URL和哈希被动式分析工具

位置参数：
  target 列出一个IP地址（接受CIDR或短划线符号），
                        URL或哈希以查询或传递文件的文件名
                        包含要查询的IP地址信息，URL或哈希
                        用换行符分隔。

可选参数：
  -h，--help显示此帮助信息并退出
  -o OUTPUT，--output OUTPUT
                        此选项将结果输出到文件。
  -b，--bot此选项将输出bot的最小化结果。
  -f CEF，--cef CEF此选项将结果输出为CEF格式文件。
  -w WEB，--web WEB此选项将结果输出到HTML文件。
  -c CSV，--csv CSV此选项将结果输出到CSV文件。
  -d DELAY，-​​-delay DELAY
                        这将改变延迟到输入的秒数。
                        默认值为2。
  -s SOURCE, --source SOURCE
                        此选项将仅针对特定源引擎运行目标以拉取关联的域
                        选项在XML配置文件中的siteelement的name属性中定义
                        可以是由分号分隔的名称列表。
  --proxy PROXY 此选项将设置要使用的代理（例如 proxy.example.com:8080）
  -a USERAGENT，--useragent USERAGENT
                        此选项允许用户设置正在使用的Web服务的user-agent
                        默认情况下，user-agent设置为Automatic / version
  -V，--vercheck 此选项检查并报告Automator的版本
                        检查包含在Automator中的每个python模块
                        默认值（no -V）为False
  -r，--refreshxml 此选项刷新远程GitHub站点上的tekdefense.xml文件。 
                        默认值（no -r）为False。
  -v，--verbose 此选项将消息打印到屏幕。
                        默认值（no -v）为False。
```

0x02 Automater用法示例
-----------------

```shell
root@kali:~# automater  -w test -v 210.41.224.132

____________________     Results found for: 210.41.224.132     ____________________
[+] A records from Robtex.com: www[.]cuit.edu.cn
No results found in the FNet URL
[+] VT ASN: 4538
[+] VT Country: CN
[+] VT AS Owner: No results found
[+] VT pDNS: ('2015-03-23 00:00:00', 'www[.]cuit.edu.cn')
[+] VT Malware: No results found
[+] VT Mal URLs: No results found
[+] Blacklist from IPVoid: No results found
[+] ISP from IPvoid: China Education and Research Networ...
[+] Country from IPVoid: (CN) China
[+] Malc0de Date: No results found
[+] Malc0de IP: No results found
[+] Malc0de Country: No results found
[+] Malc0de ASN: No results found
[+] Malc0de ASN Name: No results found
[+] Malc0de MD5: No results found
[+] Reputation Authority Score: 50/100
[+] FreeGeoIP Country Name: China
[+] FreeGeoIP Region Name: Sichuan
[+] FreeGeoIP City: Chengdu
[+] FreeGeoIP Zipcode: No results found
[+] FreeGeoIP Latitude: 30.6667
[+] FreeGeoIP Longitude: 104.0667
[+] SANS total target IPs seen: No results found
[+] SANS total packets blocked: No results found
[+] SANS last seen on: No results found
[+] SANS first seen on: No results found
No results found in the THIP
No results found in the TekHP
[+] ProjectHoneypot activity type: No results found
[+] ProjectHoneypot first mail received: No results found
[+] ProjectHoneypot last mail received: No results found
[+] ProjectHoneypot total mails received: No results found
[+] ProjectHoneypot spider first seen: No results found
[+] ProjectHoneypot spider last seen: No results found
[+] ProjectHoneypot spider sightings: No results found
[+] ProjectHoneypot user-agent sightings: No results found
[+] ProjectHoneypot first post on: No results found
[+] ProjectHoneypot last post on: No results found
[+] ProjectHoneypot form posts: No results found
[+] ProjectHoneypot first rule break on: No results found
[+] ProjectHoneypot last rule break on: No results found
[+] ProjectHoneypot rule break sightings: No results found
[+] ProjectHoneypot first dictionary attack on: No results found
[+] ProjectHoneypot last dictionary attack on: No results found
[+] ProjectHoneypot dictionary attack sightings: No results found
[+] ProjectHoneypot harvester first seen: No results found
[+] ProjectHoneypot harvester last seen: No results found
[+] ProjectHoneypot harvester sightings: No results found
[+] ProjectHoneypot harvester results: No results found

[+] Generating HTML output: test
test Generated
```


  [1]: http://www.tekdefense.com/automater/
  [2]: http://git.kali.org/gitweb/?p=packages/automater.git;a=summary