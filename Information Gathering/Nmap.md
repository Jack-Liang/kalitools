# Nmap

## Nmap包描述

Nmap（“网络映射器”）是用于网络发现和安全审计的免费和开放源（许可证）实用程序。许多系统和网络管理员还发现它对于诸如网络库存，管理服务升级调度以及监视主机或服务正常运行时间等任务很有用。Nmap以新颖的方式使用原始IP数据包来确定网络上可用的主机，这些主机提供的服务（应用程序名称和版本），它们正在运行的操作系统（和操作系统版本），什么类型的数据包过滤器/防火墙正在使用，还有几十个其他特性。它旨在快速扫描大型网络，但对单个主机工作正常。Nmap在所有主要的计算机操作系统上运行，官方二进制包可用于Linux，Windows和Mac OS X。

Nmap被Linux Journal，Info World，LinuxQuestions.Org和Codetalker Digest评为“年度安全产品”。它甚至有十二部电影，包括矩阵重装，模具硬4，女孩与龙纹身和Bourne最后通atum。

## Nmap是...

- 灵活：支持数十种先进技术，用于映射填充有IP过滤器，防火墙，路由器和其他障碍的网络。这包括许多端口扫描机制（TCP和UDP），操作系统检测，版本检测，ping扫描等。请参阅文档页。

- 强大：Nmap已被用于扫描数十万台机器的庞大网络。

- 便携式：支持大多数操作系统，包括Linux，Microsoft Windows，FreeBSD，OpenBSD，Solaris，IRIX，Mac OS X，HP-UX，NetBSD，Sun OS，Amiga等。

- 简单：虽然Nmap为高级用户提供了一组丰富的高级功能，但您可以简单地从“nmap -v -A targethost”开始。传统的命令行和图形（GUI）版本都可以满足您的偏好。二进制文件可用于那些不希望从源代码编译Nmap的用户。

- 免费：Nmap项目的主要目标是帮助使互联网更安全一些，并为管理员/审计员/黑客提供探索其网络的高级工具。Nmap可以免费下载，并附带完整的源代码，您可以根据许可证条款修改和重新分发。

- 良好的文件：重大的努力已经投入全面和最新的手册页，白皮书，教程，甚至一整本书！在这里找到多种语言。

- 支持：虽然Nmap不提供保修，但它得到了开发人员和用户的充满活力的社区的良好支持。大多数此交互发生在Nmap邮件列表上。大多数错误报告和问题应该发送到nmap-dev列表，但只有在你阅读了指南。我们建议所有用户订阅低流量nmap-hackers公告列表。你也可以在Facebook和Twitter上找到Nmap。对于实时聊天，加入Freenode或EFNet上的#nmap频道。

- 备受赞誉：Nmap赢得了无数奖项，包括“Linux年报”，“信息世界”和“Codetalker Digest”的“年度信息安全产品”。它已被数以百计的杂志文章，几部电影，几十本书和一本漫画书系列。请访问新闻页了解更多详情。

- 热门：每天有成千上万的人下载Nmap，它包含在许多操作系统（Redhat Linux，Debian Linux，Gentoo，FreeBSD，OpenBSD等）中。它是Freshmeat.Net存储库中排名前十的（30,000个）程序之一。这是很重要的，因为它给Nmap带来了充满活力的开发和用户支持社区。

资料来源：http://nmap.org/ 

[Nmap Homepage](http://insecure.org/) | [Kali Nmap Repo](http://insecure.org/)

- 作者：Fyodor

- 许可证：GPLv2

## nmap软件包中包含的工具

### nping - 网络数据包生成工具/ ping实用程序

```
root @ kali：〜＃nping -h 
Nping 0.6.40（http://nmap.org/nping）
用法：nping [探测模式] [选项] {目标规格} 

目标规范：
  目标可以指定为主机名，IP地址，网络等。
  例如：scanme.nmap.org，microsoft.com/24,192.168.0.1; 10.0。*。1-24 
PROBE MODES：-- 
  tcp-connect：Unprivileged TCP连接探测器模式。
  --tcp：TCP探测模式。
  --udp：UDP探测模式。
  --icmp：ICMP探测模式。
  --arp：ARP / RARP探测模式。
  --tr，--traceroute：
                                     Traceroute模式（只能与TCP / UDP / ICMP模式一起使用）。
TCP CONNECT MODE 
   ：-p，--dest-port <port spec>：设置目标端口。
   -g，--source-port <portnumber>：尝试使用自定义源端口。
TCP PROBE MODE：
   -g，--source-port <portnumber>：设置源端口。
   -p，--dest-port <port spec>：设置目标端口。
   --seq <seqnumber>：设置序列号。
   --flags <flag list>：设置TCP标志（ACK，PSH，RST，SYN，FIN ...）-- 
   ack <acknumber>：设置ACK号。
   --win <size>：设置窗口大小。
   --badsum：使用随机无效校验和。
UDP PROBE MODE：
   -g，--source-port <portnumber>：设置源端口。
   -p，--dest-port <port spec>：设置目标端口。
   --badsum：使用随机无效校验和。
ICMP PROBE MODE：
  -- icmp -type <type>：ICMP类型。
  --icmp-code <code>：ICMP代码。
  --icmp-id <id>：设置标识符。
  --icmp-seq <n>：设置序列号。
  --icmp-redirect-addr <addr>：设置重定向地址。
  --icmp-param-pointer <pnt>：设置参数问题指针。
  --icmp-advertisement-lifetime <time>：设置路由器通告生命周期。
  --icmp-advert-entry <IP，pref>：添加路由器广播条目。
  --icmp-orig-time <timestamp>：设置始发时间戳。
  --icmp-recv-time <timestamp>：设置接收时间戳。
  --icmp-trans-time <timestamp>：设置发送时间戳。
ARP / RARP PROBE模式：-- 
  arp-type <type>：类型：ARP，ARP应答，RARP，RARP应答。
  --arp-sender-mac <mac>：配置发送方MAC地址。
  --arp-sender-ip <addr>：设置发送方IP地址。
  --arp-target-mac <mac>：设置目标MAC地址。
  --arp-target-ip <addr>：设置目标IP地址。
IPv4选项：
  -S，--source-ip：设置源IP地址。
  --dest-ip <addr>：设置目标IP地址（用作
                                     {目标规范}的替代）。
  --tos <tos>：设置服务类型字段（8位）。
  --id <id>：设置标识字段（16位）。
  --df：设置不分段标志。
  --mf：设置更多片段标志。
  --ttl <hops>：设置生存时间[0-255]。
  --badsum-ip：使用随机无效校验和。
  --ip-options <S | R [route] | L [route] | T | U ...>：设置IP选项
  --ip-options <hex string>：
  设置IP选项--mtu <size>：设置MTU。如果MTU 
                                     足够小，则分组会碎片化。
IPv6选项：
  -6，--IPv6：使用IP版本6. 
  --dest-ip：设置目标IP地址（用作
                                     {目标规范}的替代）。
  --hop-limit：设置跳数限制（与IPv4 TTL相同）。
  --traffic-class <class>：：设置流量类。
  --flow <label>：设置流标签。
以太网选项：-- 
  dest-mac <mac>：设置目标MAC地址。
                                     （禁用ARP解析）
  --source-mac <mac>：设置源MAC地址。
  --ether类型<type>：设置EtherType值。
PAYLOAD选项：-- 
  data <hex string>：包含自定义有效内容。
  --data-string <text>：包含自定义ASCII文本。
  --data-length <len>：包含随机字节作为有效载荷。
ECHO CLIENT / SERVER：-- 
  echo-client <passphrase>：在客户端模式下运行Nping。
  --echo-server <passphrase>：在服务器模式下运行Nping。
  --echo-port <port>：使用自定义<port>来监听或连接。
  --no-crypto：禁用加密和身份验证。
  --once：一次连接后停止服务器。
  --safe-payloads：清除回应报文中的应用数据。
时间和性能：
  <time>的选项以秒为单位，或者将值附加“ms”（毫秒），
  “s”（秒），“m”（分钟）或“h” ，0.25h）。
  --delay <time>：调整探测器之间的延迟。
  --rate <rate>：每秒发送num个数据包。
MISC：
  -h，--help：显示帮助信息。
  -V，--version：显示当前版本号。
  -c，--count <n> ：在<n>轮后停止。
  -e，--interface <name>：使用提供的网络接口。
  -H，--hide-sent：不显示发送的数据包。
  -N，--no-capture：不要尝试捕获回复。
  --privileged：假设用户具有完全特权。
  --unprivileged：假设用户缺少原始套接字权限。
  --send-eth：在原始以太网层发送数据包。
  --send-ip：使用原始IP套接字发送报文。
  --bpf-filter <filter spec>：指定自定义BPF过滤器。
OUTPUT：
  -v：将详细程度级别递增1。
  -v [level]：设置详细程度级别。例如：-v4 
  -d：将调试级别递增1。
  -d [level]：设置调试级。例如：-d3 
  -q：将详细程度级别降低一级。
  -q [N]：降低冗长级别N次
  --quiet：将详细程度和调试级别设置为最小。
  --debug：将verbosity和debug设置为最大级别。
示例：
  nping scanme.nmap.org 
  nping --tcp -p 80 --flags rst --ttl 2 192.168.1.1 
  nping --icmp --icmp-type time --delay 500ms 192.168.254.254 
  nping --echo-server“public”
```


### ndiff - 用于比较Nmap扫描结果的实用程序

```
root @ kali：〜＃ndiff -h 
用法：/ usr / bin / ndiff [option] FILE1 FILE2 
比较两个Nmap XML文件并显示它们的差异列表。
差异包括主机状态更改，端口状态更改以及
服务和操作系统检测更改。

  -h，--help显示此帮助
  -v，--verbose还显示未更改的主机和端口。
  - 文本格式的文本显示输出（默认）
  - XML格式的xml显示输出
  ```
  
  ### ncat - 连接和重定向套接字
  
  ```
  root @ kali：〜＃ncat -h 
Ncat 6.40（http://nmap.org/ncat）
用法：ncat [options] [hostname] [port] 

选项占用时间假定为秒。追加“ms”为毫秒，
“s”为秒，“m”为分钟，或“h”为小时（例如500ms）。
  -4仅使用IPv4 
  -6 仅使用IPv6 
  -un，--unixsock 仅使用Unix域套接字
  -C，--crlf对EOL序列使用CRLF 
  -c，-- sh -exec <command>通过/ bin执行给定命令/ sh 
  -e，
      --exec <command>执行给定的命令--lua-exec <filename>执行给定的Lua脚本
  -g hop1 [，hop2，...   - listen绑定和侦听传入连接-k，-- keep -open在侦听模式下接受多个连接   -n，--nodns不通过DNS解析主机名   -t，--telnet回答Telnet协商   -u，--udp使用UDP而不是默认TCP       --sctp使用SCTP而不是默认TCP   -v，--verbose设置详细程度级别（可以使用多次）   -w，--wait <time>连接超时       --append-output追加而不是clobber指定输出文件       --send-only只发送数据，忽略接收; 退出EOF       - 仅限recv只接收数据，


```

### nmap - 网络映射器

```
root @ kali：〜＃nmap -h 
Nmap 6.40（http://nmap.org）
用法：nmap [扫描类型] [选项] {目标规格} 
目标规格：
  可以传递主机名，IP地址，网络等。
  例如：scanme.nmap.org，microsoft.com/24，192.168.0.1; 10.0.0-255.1-254 
  -iL <inputfilename>：从主机/网络列表输入-iR <numhost>：
  选择随机目标
  --exclude <host1 [，host2] [，host3]，...>：Exclude主机/网络
  --excludefile <exclude_file>：从文件中排除列表
HOST DISCOVERY：
  -sL：列表扫描 - 只列出要扫描的目标
  -sn：Ping扫描 - 禁用端口扫描
  -Pn：将所有主机视为联机 - 跳过主机发现
  -PS / PA / PU / PY [portlist]：TCP SYN / ACK，   IP协议扫描-b <FTP中继主机>：FTP反弹扫描 端口规范和扫描顺序   ：-p <端口范围>：仅扫描指定的端口     例如：-p22; p1-65535; -p U：53,111,137，T：21-25,80,139,8080，S：9   -F：快速模式 - 扫描比默认扫描更少的端口   -r：连续扫描端口 - 不随机化   --top-ports < >：扫描<number>最常见的端口   --port-ratio <ratio>：扫描端口比<ratio>更常见 SERVICE / VERSION检测：   -sV：探测开放端口以确定服务/版本信息   - >：设置从0（光）到9（尝试所有探头）--   version-light：   限制最可能的探测（强度2）-- version-all：尝试每个探测器（强度9）--   version-trace：显示详细版本扫描活动（用于调试） SCRIPT SCAN：   -sC：等价于--script =默认   --script = <Lua scripts>：<Lua scripts>是逗号分隔的            目录，脚本文件或脚本类别   列表--script-args = <n1 = v1，[n2 = v2，...] ：为脚本提供   参数--script-args-file = filename：在文件中提供NSE脚本参数   --script-trace：显示发送和接收的所有数据   --script-updatedb：更新脚本数据库。   --script-help = <Lua scripts>：显示关于脚本的帮助。            <Lua scripts>            是一个逗号分隔的脚本文件或脚本类别的列表。 操作系统检测：   -O：启用操作系统检测   --osscan-limit：将操作系统检测限制为有希望的目标   --osscan-guess：更积极地猜测OS 时间和性能：   采用<time>的选项以秒为单位或追加'ms' （毫秒），   “s”（秒），“m”（分钟）或“h”（小时）   -T <0-5>：设置定时模板（越高越快）--   min-hostgroup / max-hostgroup <size>：并行主机扫描组大小   --min-parallelism / max-parallelism <numprobes>：探测并行化   - -min-rtt-timeout / max-rtt-timeout / initial-rtt-timeout <time>：       指定探测往返时间。   --max-retries <尝试>：端口扫描探测重传的数目。   --host-timeout <time>：在这个长时间后放弃目标。   -scan-delay / - max-scan-delay <time>：调整探测之间的延迟   --min- rate <number>比每秒<number>每秒   --max-rate <number>：发送数据包不快于<number>每秒 FIREWALL / IDS EVASION AND SPOOFING：   -f; --mtu <val>：片段包（可选地，w /给定的MTU）   -D <decoy1，decoy2 [，ME]，...>：   Clook a scan with decoys -S <IP_Address>：Spoof source address   -e <iface >：使用指定的接口   -g / - source-port <portnum>：   使用给定的端口号--data-length <num>：将随机数据附加到发送的数据包   --ip-options <options>：发送具有指定ip选项的数据包   --ttl <val>：设置IP生存时间字段   - -spoof-mac <MAC地址/前缀/供应商名称>：欺骗您的MAC地址   --badsum：发送带有伪造TCP / UDP / SCTP校验和的数据包 OUTPUT：   -oN / -oX / -oS / -oG <file>分别以正常，XML，s | <rIpt kIddi3      和Grepable格式输出扫描到给定文件名。   -oA <basename>：一次输出三种主要格式   -v：提高详细程度（使用-vv或更高效果）   -d：提高调试级别（使用-dd或更高效果）--   reason：   脚本扫描和traceroute --datadir <dirname>：指定自定义Nmap数据文件位置   --send-eth / - send-ip：使用原始以太网帧或IP数据包发送   --privileged：假设用户是完全特权   - -unprivileged：假定用户缺少原始套接字权限   -V：打印版本号   -h：打印此帮助摘要页。 示例：   nmap -v -A scanme.nmap.org   nmap -v -sn 192.168.0.0/16 10.0.0.0/8   nmap -v -iR 10000 -Pn -p 80 查看用户手册（http://nmap.org /book/man.html）更多选项和示例 使用原始以太网帧或IP数据包发送--privileged：假设用户是完全特权 - - 特权：假设用户缺少原始套接字权限-V：打印版本号-h：打印此帮助摘要页。示例：nmap -v -A scanme.nmap.org nmap -v -sn 192.168.0.0/16 10.0.0.0/8 nmap -v -iR 10000 -Pn -p 80 查看用户手册（http://nmap.org /book/man.html）更多选项和示例 使用原始以太网帧或IP数据包发送--privileged：假设用户是完全特权 - - 特权：假设用户缺少原始套接字权限-V：打印版本号-h：打印此帮助摘要页。示例：nmap -v -A scanme.nmap.org nmap -v -sn 192.168.0.0/16 10.0.0.0/8 nmap -v -iR 10000 -Pn -p 80 查看用户手册（http://nmap.org /book/man.html）更多选项和示例



```

### nmap用法示例

扫描详细模式（-v），启用操作系统检测，版本检测，脚本扫描和traceroute （-A），针对目标IP （192.168.1.1）进行版本检测（-sV ）：

```
root @ kali：〜＃nmap -v -A -sV 192.168.1.1 

启动Nmap 6.45（http://nmap.org）在2014-05-13 18:40 MDT 
NSE：加载118脚本扫描。
NSE：脚本预扫描。
在18:40启动ARP Ping扫描
扫描192.168.1.1 [1端口] 
在18:40完成ARP Ping扫描，已过去
0.06秒（1个主机）启动1个主机的并行DNS解析。at 18:40 
完成1个主机的并行DNS解析。at 18: 
40，0.00s elapsed 启动SYN隐藏扫描在18:40 
扫描router.localdomain（192.168.1.1）[1000端口] 
发现的开放端口53 / tcp在192.168.1.1 
发现的开放端口22 / tcp在192.168.1.1 
发现在192.168.1.1上打开端口80 / tcp在192.168.1.1上
发现打开的端口3001 / tcp
```

### nping用法示例

使用TCP模式（-TCP）来探测端口22 （-p 22）使用SYN标志（-flags SYN）为2的TTL (–ttl 2) 在远程主机上（192.168.1.1） ：

```
60125 SA ttl = 64 id = 0 iplen = 44 seq = 3409166569 win = 5840 <mss 1460> SENT（3.0707s）TCP 192.168.1.15:60125> 192.168.1.1:22 S ttl = 2 id = 54240 iplen = 40 seq = 1720523417 win = 1480 RCVD（3.0710s）TCP 192.168.1.1:22> 192.168.1.15:60125 SA ttl = 64 id = 0 iplen = 44 seq = 3424813300 win = 5840 <mss 1460> SENT（4.0721s）TCP 192.168.1.15 ：60125> 192.168.1.1:22 S ttl = 2 id = 54240 iplen = 40 seq = 1720523417 win = 1480 RCVD（4.0724s）TCP 192.168.1.1:22> 192.168.1.15:60125 SA ttl = 64 id = 0 iplen = 44 seq = 3440460772 win = 5840 <mss 1460> Max rtt：0.337ms | 最小rtt：0.282ms | 平均rtt：0.296ms 发送的原始分组：5（200B）| Rcvd：5（230B）| 丢失：0（0.00％） Nping完成：1 IP地址在4.13秒内ping通 SENT（3.0707s）TCP 192.168.1.15:60125> 192.168.1.1:22 S ttl = 2 id = 54240 iplen = 40 seq = 1720523417 win = 1480 RCVD（3.0710s）TCP 192.168.1.1:22> 192.168.1.15:60125 SA ttl = 64 id = 0 iplen = 44 seq = 3424813300 win = 5840 <mss 1460> SENT（4.0721s）TCP 192.168.1.15:60125> 192.168.1.1:22 S ttl = 2 id = 54240 iplen = 40 seq = 1720523417 win = 1480 RCVD（4.0724s）TCP 192.168.1.1:22> 192.168.1.15:60125 SA ttl = 64 id = 0 iplen = 44 seq = 3440460772 win = 5840 <mss 1460> Max rtt：0.337ms | 最小rtt：0.282ms | 平均rtt：0.296ms 发送的原始分组：5（200B）| Rcvd：5（230B）| 丢失：0（0.00％）Nping完成：1 IP地址在4.13秒内ping通 SENT（3.0707s）TCP 192.168.1.15:60125> 192.168.1.1:22 S ttl = 2 id = 54240 iplen = 40 seq = 1720523417 win = 1480 RCVD（3.0710s）TCP 192.168.1.1:22> 192.168.1.15:60125 SA ttl = 64 id = 0 iplen = 44 seq = 3424813300 win = 5840 <mss 1460> SENT（4.0721s）TCP 192.168.1.15:60125> 192.168.1.1:22 S ttl = 2 id = 54240 iplen = 40 seq = 1720523417 win = 1480 RCVD（4.0724s）TCP 192.168.1.1:22> 192.168.1.15:60125 SA ttl = 64 id = 0 iplen = 44 seq = 3440460772 win = 5840 <mss 1460> Max rtt：0.337ms | 最小rtt：0.282ms | 平均rtt：0.296ms 发送的原始分组：5（200B）| Rcvd：5（230B）| 丢失：0（0.00％）Nping完成：1 IP地址在4.13秒内ping通 168.1.1：22> 192.168.1.15:60125 SA ttl = 64 id = 0 iplen = 44 seq = 3424813300 win = 5840 <mss 1460> SENT（4.0721s）TCP 192.168.1.15:60125> 192.168.1.1:22 S ttl = 2 id = 54240 iplen = 40 seq = 1720523417 win = 1480 RCVD（4.0724s）TCP 192.168.1.1:22> 192.168.1.15:60125 SA ttl = 64 id = 0 iplen = 44 seq = 3440460772 win = 5840 <mss 1460 > Max rtt：0.337ms | 最小rtt：0.282ms | 平均rtt：0.296ms 发送的原始分组：5（200B）| Rcvd：5（230B）| 丢失：0（0.00％）Nping完成：1 IP地址在4.13秒内ping通 168.1.1：22> 192.168.1.15:60125 SA ttl = 64 id = 0 iplen = 44 seq = 3424813300 win = 5840 <mss 1460> SENT（4.0721s）TCP 192.168.1.15:60125> 192.168.1.1:22 S ttl = 2 id = 54240 iplen = 40 seq = 1720523417 win = 1480 RCVD（4.0724s）TCP 192.168.1.1:22> 192.168.1.15:60125 SA ttl = 64 id = 0 iplen = 44 seq = 3440460772 win = 5840 <mss 1460 > Max rtt：0.337ms | 最小rtt：0.282ms | 平均rtt：0.296ms 发送的原始分组：5（200B）| Rcvd：5（230B）| 丢失：0（0.00％）Nping完成：1 IP地址在4.13秒内ping通 60125 SA ttl = 64 id = 0 iplen = 44 seq = 3440460772 win = 5840 <mss 1460> Max rtt：0.337ms | 最小rtt：0.282ms | 平均rtt：0.296ms 发送的原始分组：5（200B）| Rcvd：5（230B）| 丢失：0（0.00％）Nping完成：1 IP地址在4.13秒内ping通 60125 SA ttl = 64 id = 0 iplen = 44 seq = 3440460772 win = 5840 <mss 1460> Max rtt：0.337ms | 最小rtt：0.282ms | 平均rtt：0.296ms 发送的原始分组：5（200B）| Rcvd：5（230B）| 丢失：0（0.00％）Nping完成：1 IP地址在4.13秒内ping通




```

### ndiff用法示例

比较昨天的端口扫描（yesterday.xml）与从今天（today.xml）的扫描：

```
root @ kali：〜＃ndiff yesterday.xml today.xml 
-Nmap 6.45 scan started Tue May 13 18:46:43 2014 as：nmap -v -F -oX yesterday.xml 192.168.1.1 
+ Nmap 6.45 scan initiated Tue May 13 18:47:58 2014 as：nmap -v -F -oX today.xml 192.168.1.1 

 endian.localdomain（192.168.1.1，00：01：6C：6F：DD：D1）：
未显示：96个过滤端口
+未显示：97过滤的端口
 PORT STATE服务版本
-22 / tcp打开ssh
 ```
 
 ### ncat用法示例
 
 要详细（-v） ，运行/ bin /在连接庆典（-exec“/斌/ bash中”） ，只允许1个IP地址（-ALLOW 192.168.1.123） ，听TCP端口4444上（-l 4444） ，和保持侦听器断开连接（-keep-open）：
 
 ```
 root @ kali：〜＃ncat -v --exec“/ bin / bash”--allow 192.168.1.123 -l 4444 --keep-open 
Ncat：Version 6.45（http://nmap.org/ncat）
Ncat：Listening on ::: 4444 
Ncat：正在侦听
0.0.0.0:4444 Ncat：从192.168.1.123连接。
Ncat：连接从192.168.1.123:39501。
Ncat：从192.168.1.15连接。
Ncat：连接从192.168.1.15:60393。
Ncat：新连接被拒绝：不允许
```


 
