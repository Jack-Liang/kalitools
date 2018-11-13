---
title: dnsenum
categories: Information Gathering
tags: [dns,kali linux,dnsenum,information gathering,recon]
date: 2016-10-20 11:00:00
---
0x00 dnsenum介绍
-------------

多线程perl脚本枚举域的DNS信息并发现非连续的IP段工具

主要功能：
```plain
 - 获取主机的地址（A记录）
 - 获取名称服务器（线程）
 - 获取MX记录（线程化）
 - 对名称服务器执行axfr查询并获取BIND VERSION（线程化）
 - 通过Google抓取获取额外的名称和子域(google query = “allinurl: -www site:domain”)
 - 读取文件爆破子域，也可以对具有NS记录的子域执行递归查询（开启所有线程）
 - 计算C类域网络范围并对其执行whois查询（线程化）
 - 对网络（C类或/和whois网络）执行反向查找（线程化）
 - 将ip段写入domain_ips.txt文件
```

工具来源：https://github.com/fwaeytens/dnsenum

[dnsenum主页][1] | [Kali dnsenum Repo仓库][2]

 - 作者：Filip Waeytens, tix tixxDZ
 - 证书：GPLv2

0x01 dnsenum功能
---------------

```shell
root@kali:~# dnsenum -h
dnsenum.pl VERSION:1.2.3
用法：dnsenum.pl [选项] <域>
[选项]：
注意：'-f'选项是用于穷举爆破的
一般选项：
  --dnsserver <server>   将此DNS服务器用于A，NS和MX查询
  --enum                 快捷方式选项相当于--threads 5 -s 15 -w
  -h，--help             打印此帮助消息
  --noreverse            跳过反向查找操作
  --nocolor              禁用ANSIColor输出
  --private              显示并在文件domain_ips.txt的末尾保存私有IP
  --subfile <file>       将所有有效的子域写入此文件
  -t，--timeout <value>  tcp和udp超时值（以秒为单位，默认值：10s）
  --threads <value>      将执行不同查询的线程数
  -v，--verbose          详细信息：显示所有进度和所有错误消息。
Google抓取选项：
  -p，--pages <value>    抓取名称时要处理的Google搜索页面数，默认值为5页，必须指定-s开关
  -s，--scrap <value>    将从Google抓取的子域的最大数量（默认值为15）
子域穷举选项：
  -f，--file <file>      从此文件读取子域进行爆破
  -u，--update <a|g|r|z> 向使用-f开关指定的文件更新有效的子域
        a（all）         使用所有结果更新。
        g                仅使用Google抓取结果更新
        r                仅使用反向查找结果进行更新
        z                仅使用zonetransfer结果更新
  -r，--recursion        递归子域，穷举具有NS记录的所有子域
WHOIS网络选项：
  -d，--delay <value>    在whois查询之间等待的最大值（秒），该值自定义，默认值：3s
  -w，--whois            在c类网络范围上执行whois查询
                         **警告**：这可能会产生非常大的网络流量，它需要大量的时间来执行反向查找
反向查找选项：
  -e，--exclude <regexp> 从反向查找结果中排除与regexp表达式匹配的PTR记录，对无效主机名非常有用
输出选项：
  -o --output <file>     以XML格式输出，以便可以在MagicTree中导入（www.gremwell.com）
```

0x02 dnsenum用法示例
-----------------

```shell
root@kali:~# dnsenum -f possible_subdomain.txt --subfile subdomain.txt --threads 2 -w -r cuit.edu.cn
dnsenum.pl VERSION:1.2.3
Warning: can't load Net::Whois::IP module, whois queries disabled.

-----   cuit.edu.cn   -----


Host's addresses:
__________________



Name Servers:
______________

dns.cuit.edu.cn.                         5        IN    A        210.41.224.33


Mail (MX) Servers:
___________________

mailw.cuit.edu.cn.                       5        IN    A        210.41.224.45


Trying Zone Transfers and getting Bind Versions:
_________________________________________________

unresolvable name: dns2.cuit.edu.cn at /usr/bin/dnsenum line 842 thread 2.

Trying Zone Transfer for cuit.edu.cn on dns2.cuit.edu.cn ... 
AXFR record query failed: no nameservers

Trying Zone Transfer for cuit.edu.cn on dns.cuit.edu.cn ... 
AXFR record query failed: REFUSED


Brute forcing with possible_subdomain.txt:
___________________________________________

www.cuit.edu.cn.                         5        IN    A        210.41.224.132
wlzf.cuit.edu.cn.                        5        IN    A        210.41.225.229
acm.cuit.edu.cn.                         5        IN    A        210.41.225.250
wlcc.cuit.edu.cn.                        5        IN    A        210.41.228.67
jhcwc.cuit.edu.cn.                       5        IN    A        210.41.224.220
bylw.cuit.edu.cn.                        5        IN    A        210.41.224.237
pkxt.cuit.edu.cn.                        5        IN    A        210.41.229.132
pan.cuit.edu.cn.                         5        IN    A        210.41.224.210
dzgcxy.cuit.edu.cn.                      5        IN    A        210.41.224.220
kzgcxy.cuit.edu.cn.                      5        IN    A        210.41.224.220
yjsc.cuit.edu.cn.                        5        IN    A        210.41.225.22
hqc.cuit.edu.cn.                         5        IN    A        210.41.224.220
wpgz.cuit.edu.cn.                        5        IN    A        210.41.229.135
jszx.cuit.edu.cn.                        5        IN    A        210.41.225.21
xyw.cuit.edu.cn.                         5        IN    A        210.41.224.220
gjjl.cuit.edu.cn.                        5        IN    A        210.41.224.220
math.cuit.edu.cn.                        5        IN    A        210.41.224.220
jwc.cuit.edu.cn.                         5        IN    A        210.41.225.108
jxpt.cuit.edu.cn.                        5        IN    A        210.41.228.119
wlcc.cuit.edu.cn.                        5        IN    A        210.41.228.67
xsc.cuit.edu.cn.                         5        IN    A        210.41.224.206
exam.cuit.edu.cn.                        5        IN    A        222.18.158.220


Performing recursion:
______________________


 ---- Checking subdomains NS records ----

  Can't perform recursion no NS records.


cuit.edu.cn class C netranges:
_______________________________

 210.41.224.0/24
 210.41.225.0/24
 210.41.228.0/24
 210.41.229.0/24
 222.18.158.0/24


Performing reverse lookup on 1280 ip addresses:
________________________________________________

34.224.41.210.in-addr.arpa.              86400    IN    PTR      dnsu.cuit.edu.cn.
36.224.41.210.in-addr.arpa.              86400    IN    PTR      dns.cuit.edu.cn.
40.224.41.210.in-addr.arpa.              86400    IN    PTR      jwc.cuit.edu.cn.
130.224.41.210.in-addr.arpa.             86400    IN    PTR      www.cuit.edu.cn.
131.224.41.210.in-addr.arpa.             86400    IN    PTR      ftp.cuit.edu.cn.
130.224.41.210.in-addr.arpa.             86400    IN    PTR      dep.cuit.edu.cn.
206.224.41.210.in-addr.arpa.             86400    IN    PTR      xsc.cuit.edu.cn.
```


  [1]: https://github.com/fwaeytens/dnsenum
  [2]: https://github.com/fwaeytens/dnsenum