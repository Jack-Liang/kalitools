# THC-IPV6软件包描述

一套完整的工具，可以攻击IPV6和ICMP6固有的协议弱点，并且包含一个易于使用的数据包生产库。

资料来源：https：//www.thc.org/thc-ipv6/

[THC-IPV6主页](https://www.thc.org/thc-ipv6/) | [Kali THC-IPV6资源](http://git.kali.org/gitweb/?p=packages/thc-ipv6.git;a=summary)

- 作者：The Hacker’s Choice
- 许可证：AGPLv3

## THC-IPV6包含的工具
### 6to4test.sh - 测试IPv4目标是否有激活的动态6to4隧道
```
root@kali:~# 6to4test.sh
语法: /usr/bin/6to4test.sh interface ipv4address
这个小脚本测试IPv4目标是否有激活的动态6to4隧道
需要thc-ipv6的address6和thcping6工具 
```
### address6 - 将mac或ipv4地址转换为ipv6地址
```
root@kali:~# address6
address6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法:
    address6 mac-address [ipv6-prefix]
    address6 ipv4-address [ipv6-prefix]
    address6 ipv6-address

将mac或ipv4地址转换为ipv6地址（如果没有给定第二个选项作为前缀，则使用本地的），或者当给出ipv6地址时，
打印mac或ipv4地址。 输出所有可能的变化。 出错时返回-1或已转换的结果数量
```
### alive6 - 显示分段中的活动地址
```
root@kali:~# alive6
alive6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法: alive6 [-I srcip6] [-i file] [-o file] [-DM] [-p] [-F] [-e opt] [-s port,..] [-a port,..] 
        [-u port,..] [-W TIME] [-dlrvS] interface [unicast-or-multicast-address [remote-router]]
        
显示分段中的活动地址。如果指定了远程路由器，则数据包以分段前缀的路由首部发送
选项：
  -i file           从输入文件检查系统
  -o file           结果写入输出文件
  -M                从输入地址枚举硬件地址（MAC）（慢！）
  -D                从输入地址枚举DHCP地址空间
  -p                发送ping数据包进行活跃检查（默认）
  -e dst,hop        发送一个错误数据包：目标（默认），逐跳
  -s port,port,..   发送TCP-SYN报文到端口进行活跃检查
  -a port,port,..T  发送TCP-ACK报文到端口进行活跃检查
  -u port,port,..   发送UDP数据包到端口进行活跃检查
  -d                DNS解析活跃的ipv6地址
  -n number         每个数据包的发送频率（默认值：本地1、远程2）
  -W time           发送数据包后等待的时间-毫秒（默认值：1）
  -S                慢速模式，为每个远程目标获取最佳路由或当不存在代理时
  -I srcip6         使用指定的IPv6地址作为源
  -l                使用本地链接地址而不是全局地址
  -v                详细信息（vv：更详细信息，vvv：转储所有数据包）
命令行或输入文件中的目标地址可以包括如下形式的范围
2001:db8::1-fff或2001:db8::1-2:0-ffff:0:0-ffff，等等
出错时返回-1，如果找到的系统是活跃的返回0，什么也没找到则返回1。
```
### covert_send6 - 将文件内容隐秘地发送到目标
```
root@kali:~# covert_send6
covert_send6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法: covert_send6 [-m mtu] [-k key] [-s resend] interface target file [port]
选项：
   -m mtu       指定最大MTU（默认值：interface MTU，min：1000）
   -k key       用Blowfish-160加密内容
   -s resend    每个分组发送resend次，默认值：1

将文件的内容隐秘地发送到目标，并且其POC - 除比较复杂外 - 刚好放入目标首部。
```
### covert_send6d - 将隐秘接收的内容写入文件
```
root@kali:~# covert_send6d
covert_send6d v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：covert_send6d [-k key] interface file

选项：
   -k key   用Blowfish-160解密内容

将隐秘接收的内容写入文件。
```
### denial6 - 对目标执行各种拒绝服务攻击
```
root@kali:~# denial6
denial6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：denial6 interface destination test-case-number

对目标执行各种拒绝服务攻击。
如果系统是易受攻击的，则这可导致系统崩溃或重载，所以要小心！
如果没有提供test-case-number，则只显示攻击列表。
```
### detect-new-ip6 - 此工具可以检测加入本地网络的新ipv6地址
```
root@kali:~# detect-new-ip6
detect-new-ip6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：detect-new-ip6 interface [script]

此工具可以检测加入本地网络的新ipv6地址。
如果提供了脚本，则首先对检测到的IPv6地址执行此脚本，
然后再对接口执行。
```
### detect_sniffer6 - 测试本地LAN上的系统是否正在被嗅探
```
root@kali:~# detect_sniffer6
detect_sniffer6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：detect_sniffer6 interface [target6]

测试本地LAN上的系统是否正在被嗅探。
适用于Windows、Linux、OS/X和*BSD
如果没有给出目标，则使用link-local-all-nodes地址，但是很少有效。
```
### dnsdict6 - 枚举DNS条目的域
```
root@kali:~# dnsdict6
dnsdict6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：dnsdict6 [-d46] [-s | -m | -l | -x] [-t THREADS] [-D] domain [dictionary-file]

枚举DNS条目的域，如果提供了它使用字典文件，
否则使用内置列表。这个工具是基于gnucitizen.org的dnsmap。

选项：
 -4         转储IPv4地址
 -t NO      指定要使用的线程数（默认值：8，最大值：32）。
 -D         转储选定的内置字列表，不进行扫描。
 -d         显示NS和MX类型DNS域的IPv6信息。
 -S         执行SRV服务名猜解
 -[smlx]    选择字典大小：-s（小=50）、-m（中=796）（默认）
            -l（大=1416）、-x（极大=3211）
```
### dnsrevenum6 - 执行快速反向DNS枚举，并能够应对慢速服务器
```
root@kali:~# dnsrevenum6
dnsrevenum6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：dnsrevenum6 dns-server ipv6address

执行快速反向DNS枚举，并能够应对慢速服务器。
例子：
  dnsrevenum6 dns.test.com 2001:db8:42a8::/48
  dnsrevenum6 dns.test.com 8.a.2.4.8.b.d.0.1.0.0.2.ip6.arpa
```
### dnssecwalk - 执行DNSSEC NSEC漫游
```
root@kali:~# dnssecwalk
dnssecwalk v1.2 (c) 2013 by Marc Heuse <mh@mh-sec.de> http://www.mh-sec.de

语法：dnssecwalk [-e46] dns-server domain

选项：
 -e     确保域位于找到的地址中，否则退出
 -4     解析找到条目的IPv4地址
 -6     解析找到条目的IPv6地址

执行DNSSEC NSEC漫游。

示例：dnssecwalk dns.test.com test.com
```
### dos_mld.sh - 如果指定，将首先丢弃目标的多播地址
```
root@kali:~# dos_mld.sh
语法：/usr/bin/dos_mld.sh [-2] interface [target-link-local-address multicast-address]
如果指定，目标的多播地址将首先丢弃。
所有的组播流量都会在一段时间后停止。
指定-2选项使用MLDv2。
```
### dos-new-ip6 - 此工具可阻止新的ipv6接口出现
```
root@kali:~# dos-new-ip6
dos-new-ip6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：dos-new-ip6 interface

这个工具通过发送重复ip6检查（DAD）应答来阻止新的ipv6接口出现。
这导致对新ipv6设备的DOS攻击。
```
### dump_router6 - 转储所有本地路由器信息
```
root@kali:~# dump_router6
dump_router6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：dump_router6 interface

转储所有本地路由器信息
```
### exploit6 - 对目标执行各种CVE已知的IPv6漏洞利用
```
root@kali:~# exploit6
exploit6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：exploit6 interface destination [test-case-number]

对目标执行各种CVE已知的IPv6漏洞利用
请注意，对于可利用的溢出，仅使用“AAA...”字符串。
如果一个系统很脆弱，那么它会崩溃，所以要小心！
```
### extract_hosts6.sh - 打印文件中IPv6地址的主机部分
```
root@kali:~# extract_hosts6.sh
/usr/bin/extract_hosts6.sh FILE
打印文件中IPv6地址的主机部分
```
### extract_networks6.sh - 打印文件中找到的网络
```
root@kali:~# extract_networks6.sh
/usr/bin/extract_networks6.sh FILE
打印文件中找到的网络
```
### fake_advertise6 - 在网络上公告ipv6地址
```
root@kali:~# fake_advertise6
fake_advertise6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：fake_advertise6 [-DHF] [-Ors] [-n count] [-w seconds] interface 
     ip-address-advertised [target-address [mac-address-advertised [source-ip-address]]]

在网络上公告ipv6地址（如果没有指定，则使用自己的mac），
如果没有设置目标地址，则将其发送到全节点多播地址。
源IP地址未设置时使用发送者地址。

发送选项：
  -n count      发送多少包（默认：永远）
  -w seconds    发送数据包之间的等待时间（默认值：5）
标志选项：
  -O            不设置覆盖标志（默认：开）
  -r            设置路由标志（默认：关）
  -s            设置请求标志（默认：关）
ND安全漏洞选项（可以组合）：
  -H            添加一个逐跳首部
  -F            添加一个单次片段首部（可以指定多次）
  -D            添加一个大的目标首部，分片数据包。
```
### fake_dhcps6 - 假冒DHCPv6服务器
```
root@kali:~# fake_dhcps6
fake_dhcps6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：fake_dhcps6 interface network-address / prefix-length dns-server 
                 [dhcp-server-ip-address [mac-address]]

假冒DHCPv6服务器，用于配置地址并设置DNS服务器
```
### fake_dns6d - 假冒DNS服务器，为任何查找请求提供相同的ipv6地址
```
root@kali:~# fake_dns6d
fake_dns6d v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：fake_dns6d interface ipv6-address [fake-ipv6-address [fake-mac]]
假冒DNS服务器为任何查找请求提供相同的ipv6地址
如果客户端具有固定的DNS服务器，则可以将其与parasite6一起使用
注意：服务器非常简单。不支持数据包中的多重查询，也不支持NS、MX等查询。
```
### fake_dnsupdate6 - 假冒DNS更新程序
```
root@kali:~# fake_dnsupdate6
fake_dnsupdate6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：fake_dnsupdate6 dns-server full-qualified-host-dns-name ipv6address

示例：fake_dnsupdate6 dns.test.com myhost.sub.test.com ::1
```
### fake_mipv6 - 将家乡地址所有数据包重定向到转交地址
```
root@kali:~# fake_mipv6
fake_mipv6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：fake_mipv6 interface home-address home-agent-address care-of-address

如果移动IPv6归属代理被误配置为不使用IPSEC接受MIPV6更新，
则将家乡地址所有数据包重定向到转交地址
```
### fake_mld26
```
root@kali:~# fake_mld26
fake_mld26 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：fake_mld26 [-l] interface add | delete | query [multicast-address 
[target-address [ttl [own-ip [own-mac-address [destination-mac-address]]]]]]

使用MLDv2协议。只有协议功能的一个子集可以通过命令行来实现。如果您需要某些东西，请编写代码。
可在您选择的多播组中公告或删除自己 - 或任何您想要的人，查询网络上谁正在监听组播地址。
使用-l选项来循环发送（以5秒为间隔），直到按下Control-C。
```
### fake_mld6 - 公告或删除自己 - 或任何你想要的人
```
root@kali:~# fake_mld6
fake_mld6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：fake_mld6 [-l] interface add | delete | query [multicast-address 
[target-address [ttl [own-ip [own-mac-address [destination-mac-address]]]]]]

在您选择的多播组中公告或删除自己 - 或任何您想要的人，查询网络上谁正在监听组播地址。
使用-l选项来循环发送（以5秒为间隔），直到按下Control-C。
```
### fake_mldrouter6 - 宣告、删除或索取MLD路由器
```
root@kali:~# fake_mldrouter6
fake_mldrouter6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：fake_mldrouter6 [-l] interface advertise | solicitate | terminate 
                     [own-ip [own-mac-address]]

宣告、删除或索取MLD路由器 - 自己或其他人。
使用-l选项来循环发送（以5秒为间隔），直到按下Control-C。
```
### fake_pim6
```
root@kali:~# fake_pim6
fake_pim6 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：
  fake_pim6 [-t ttl] [-s src6] [-d dst6] interface hello [dr_priority]
  fake_pim6 [-t ttl] [-s src6] [-d dst6] interface join | prune neighbor6 multicast6 target6

hello命令可选DR优先级（默认值：0）。
join和prune命令需要多播组来修改加入或离开邻近PIM路由器的目标地址。
使用-s来欺骗源ip6，-d发送到ff02::d以外的另一个地址，-t设置不同的TTL（默认值：1）
```
### fake_router26 - 宣告自己为路由器，并尝试成为默认路由器
```
root@kali:~# fake_router26
fake_router26 v2.3 (c) 2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：fake_router26 [-E type] [-A network/prefix] [-R network/prefix] 
              [-D dns-server] [-s sourceip] [-S sourcemac] [-ardl seconds]
              [-Tt ms] [-n no] [-i interval] interface

选项：
 -A network/prefix  添加自动配置网络（最多16次）
 -a seconds         -A前缀的有效生命周期（默认为99999）
 -R network/prefix  添加路由条目（最多16次）
 -r seconds         -R路由条目生存期（默认为4096）
 -D dns-server      指定DNS服务器（最多16次）
 -L searchlist      指定DNS域搜索列表，用逗号分隔
 -d seconds         -D的dns条目生存期（默认为4096）
 -M mtu             要发送的MTU，默认为接口设置
 -s sourceip        路由器的源IP，默认为本地连接
 -S sourcemac       路由器的源MAC，默认为您的接口
 -l seconds         路由器生命周期（默认为2048）
 -T ms              可达定时器（默认为0）
 -t ms              重发定时器（默认为0）
 -p priority        优先级"low"、"medium"、"high" (默认)、"reserved"
 -F flags           设置一个或多个以下标志：managed，other，homeagent, 
                    proxy, reserved; 用逗号分隔
 -E type            路由器通告守护躲避选项。类型：
     H              简单的逐跳首部
     1              简单的一次分片首部（可以添加多个）
     D              插入一个大的目标首部
     O              重叠片段用于keep-first目标（Win，BSD，Mac）
     o              重叠片段用于keep-last目标（Linux，Solaris）
                    示例: -E H111, -E D
 -m mac-address     是否应当只有一台机器接收RA（不与-E DoO同用）
 -i interval        RA包时间间隔（默认值：5）
 -n number          要发送的RA数量（默认：无限制）

宣告自己为路由器，并尝试成为默认路由器。
如果提供了不存在的本地链接或mac地址，则会导致DOS。
```
### fake_router6 - 宣布自己作为路由器，并尝试成为默认路由器。*****************************************
```
root @ kali：〜＃fake_router6
fake_router6 v2.3（c）2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：fake_router6 [-HFD] interface network-address / prefix-length [dns-server [router-ip-link-local [mtu [mac-address]]]]

宣布自己为路由器，并尝试成为默认路由器。
如果提供了不存在的链接本地或mac地址，则会导致DOS。
选项-H添加逐跳，-F碎片头和-Ddst头。
fake_solicitate6 - 在网络上解析ipv6地址
root @ kali：〜＃fake_solicitate6
fake_solicitate6 v2.3（c）2013年由van Hauser / THC <vh@thc.org> www.thc.org

语法：fake_solicitate6 [-DHF] interface ip-address-solicitated [target-address [mac-address-solicitated [source-ip-address]]]

在网络上解析ipv6地址，将其发送到全节点组播地址
firewall6 - 执行各种ACL旁路尝试来检查实现
root @ kali：〜＃firewall6
firewall6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：firewall6 [-u] interface destination port [test-case-no]

执行各种ACL旁路尝试来检查实现。
默认为TCP端口，选项-u切换到UDP。
对于所有测试用例来说，必须允许ICMPv6 ping到目的地。
flood_advertise6 - 用邻居广告洪泛本地网络
root @ kali：〜＃flood_advertise6
flood_advertise6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：flood_advertise6接口

用邻居广告洪泛本地网络。
flood_dhcpc6 - DHCP客户端flooder
root @ kali：〜＃flood_dhcpc6
flood_dhcpc6 v2.3（c）2013年由van Hauser / THC <vh@thc.org> www.thc.org

语法：flood_dhcpc6 [-n | -N] [-1] [-d] interface [domain-name]

DHCP客户端flooder。用于耗尽DHCP6服务器的IP地址池
提供。注意：如果游泳池非常大，这是毫无意义的。 :-)

默认情况下，链路本地IP MAC地址是随机的，但是这将不起作用
在某些情况下。 -n将使用真正的MAC，-N真正的MAC和
链接本地地址。 -1只会解析一个地址，但不要求它。
如果不使用-N，应该并行运行寄生虫6。
使用-d强制DNS更新，您可以在命令行中指定一个域名。
flood_mld26 - 使用MLDv2报告洪泛本地网络
root @ kali：〜＃flood_mld26
flood_mld26 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：flood_mld26接口

用MLDv2报告洪泛本地网络。
flood_mld6 - 用MLD报告洪泛本地网络
root @ kali：〜＃flood_mld6
flood_mld6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：flood_mld6接口

用MLD报告洪泛本地网络。
flood_mldrouter6 - 用MLD路由器通告洪泛本地网络
root @ kali：〜＃flood_mldrouter6
flood_mldrouter6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：flood_mldrouter6接口

用MLD路由器通告洪泛本地网络。
flood_router26 - 使用路由器广告洪泛本地网络
root @ kali：〜＃flood_router26
flood_router26 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：flood_router26 [-HFD] [-s] [-RPA]界面

用路由器通告来洪泛本地网络。
每个数据包包含17个前缀和路由令
-F / -D / -H添加fragment / destination / hopbyhop头来绕过RA guard安全。
-R只发送路由条目，没有前缀信息。
-P只发送前缀信息，没有路由条目。
-A就像-P，但是实现了George Kargiotakis的攻击以禁用隐私扩展
选项-s使用小的寿命，造成更为严重的影响
flood_router6 - 使用路由器通告来淹没本地网络
root @ kali：〜＃flood_router6
flood_router6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：flood_router6 [-HFD]界面

用路由器通告来洪泛本地网络。
-F / -D / -H添加fragment / destination / hopbyhop头来绕过RA guard安全。
flood_solicitate6 - 用邻居请求洪泛网络
root @ kali：〜＃flood_solicitate6
flood_solicitate6 v2.3（c）2013 van van Hauser / THC <vh@thc.org> www.thc.org

语法：flood_solicitate6 interface [target]

用邻居招揽网络。
fragmentation6 - 执行片段防火墙和实现检查
root @ kali：〜＃fragmentation6
碎片6 v2.3（c）2013年，van Hauser / THC <vh@thc.org> www.thc.org

语法：fragmentation6 [-fp] [-n number] interface destination [test-case-no]

-f激活洪水模式，发送之间不会暂停; -p首先禁用
最终ping，-n数字指定每个测试执行的频率

执行片段防火墙和实施检查，包括拒绝服务
fuzz_ip6 - 模糊一个icmp6数据包
root @ kali：〜＃fuzz_ip6
fuzz_ip6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：fuzz_ip6 [-x] [-t number | -T number] [-p number] [-IFSDHRJ] [-X | -1 | -2 | -3 | -4 | -5 | -6 | -7 | -8 | -9 | -0 port]接口单播-or-multicast-address [address-in-data-pkt]

模糊一个icmp6数据包
选项：
 -X不要添加任何ICMP / TCP头（tranport laye）
 -1模糊ICMP6回显请求（默认）
 -2 fuzz ICMP6邻居招揽
 -3模糊ICMP6邻居广告
 -4模糊ICMP6路由器广告
 -5 fuzz组播监听报告报文
 -6 fuzz组播侦听器完成数据包
 -7 fuzz组播侦听器查询报文
 -8 fuzz组播侦听器v2报文包
 -9fuzz组播侦听器v2查询报文
 -0 fuzz节点查询包
 -s端口模糊TCP-SYN数据包对端口
 -x尝试所有256个值用于标志和字节类型
 -t号码从测试号码继续。数
 -T号只执行测试号。数
 -p号码执行一个活动检查每次测试（默认值：无）
  - 不要执行初始和最终的活动测试
 -n数字发送每个数据包的次数（默认值：1）
 我也模糊了IP头
 -F添加一次分片，并将其模糊（1）
 -S添加源路由，并将其模糊（1）
 -D添加目标头，并且它也是模糊的（1）
 -H添加逐跳标题，并且它也是模糊的（对于1和5-9）
 -R添加路由器警报头，并将其模糊（5-9和全部）
 -J添加巨型数据包头，并将其模糊（1）
您只能定义-0 ... -9和-s之一，默认为-1。
返回-1错误，0测试完成和targt活着或1对目标崩溃。
implementation6 - 执行一些ipv6实现检查
root @ kali：〜＃implementation6
实施6 v2.3（c）2013年，van Hauser / THC <vh@thc.org> www.thc.org

语法：implementation6 [-p] [-s sourceip6] interface destination [test-case-number]

选项：
  -s sourceip6使用指定的源IPv6地址
  -p不要在开始和结束执行活动检查
执行一些ipv6实现检查，可以用来测试一些
防火墙功能也。接近2分钟即可完成
implementation6d - 通过实现6工具识别测试包
root @ kali：〜＃implementation6d
实施6d v2.3（c）2013年，van Hauser / THC <vh@thc.org> www.thc.org

语法：implementation6d接口

通过实现6工具识别测试包，有用的是检查什么
数据包通过防火墙
inject_alive6 - 此工具可解答PPPoE和6in4隧道上的保持活动请求
root @ kali：〜＃inject_alive6
inject_alive6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：inject_alive6 [-ap]接口

此工具可解答PPPoE和6in4隧道上的保持活动请求;用于PPPoE
它还发送keep-alive请求。
请注意，必须设置适当的环境变量THC_IPV6_ {PPPOE | 6IN4}
选项-a将每15秒主动发送活动请求。
选项-p不会发送对活动请求的回复。
inverse_lookup6 - 执行反向地址查询
root @ kali：〜＃reverse_lookup6
reverse_lookup6 v2.3（c）2013 van van Hauser / THC <vh@thc.org> www.thc.org

语法：reverse_lookup6接口mac-address

执行反向地址查询，获取分配的IPv6地址
到MAC地址。请注意，只有少数系统支持这一点。
kill_router6 - 宣布一个目标路由器下来将其从路由表中删除
root @ kali：〜＃kill_router6
kill_router6 v2.3（c）2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：kill_router6 [-HFD] interface router-address [srcmac [dstmac]]

宣布目标路由器下一步将其从路由表中删除。
如果您提供“*”作为路由器地址，则此工具将嗅探任何网络
RA数据包并立即发送kill数据包。
选项-H添加逐跳，-F碎片头和-Ddst头。
ndpexhaust26 - 使用ICMPv6 TooBig错误消息来淹没目标/ 64网络
root @ kali：〜＃ndpexhaust26
ndpexhaust26 v2.3（c）2013年由van Hauser / THC <vh@thc.org> www.thc.org

语法：ndpexhaust26 [-acpPTUrR] [-s sourceip6]接口target-network

选项：
  - 添加一个路由器警报的逐跳标头
 -c不计算校验和以节省时间
 -p发送ICMPv6回显请求
 -P发送ICMPv6回显
 -T发送ICMPv6生存时间
 -U发送ICMPv6 Unreachable（无路由）
 -r将您的/ 64前缀的源随机化
 -R将源完全随机化
 -s sourceip6使用此作为源ipv6地址

使用ICMPv6 TooBig错误消息来淹没目标/ 64网络。
这个工具版本比ndpexhaust6更有效。
ndpexhaust6 - 使用ICMPv6 TooBig错误消息来洪泛目标/ 64网络
root @ kali：〜＃ndpexhaust26
ndpexhaust26 v2.3（c）2013年由van Hauser / THC <vh@thc.org> www.thc.org

语法：ndpexhaust26 [-acpPTUrR] [-s sourceip6]接口target-network

选项：
  - 添加一个路由器警报的逐跳标头
 -c不计算校验和以节省时间
 -p发送ICMPv6回显请求
 -P发送ICMPv6回显
 -T发送ICMPv6生存时间
 -U发送ICMPv6 Unreachable（无路由）
 -r将您的/ 64前缀的源随机化
 -R将源完全随机化
 -s sourceip6使用此作为源ipv6地址

使用ICMPv6 TooBig错误消息来淹没目标/ 64网络。
这个工具版本比ndpexhaust6更有效。
root @ kali：〜＃ndpexhaust6
ndpexhaust6 by mario fleischmann <mario.fleischmann@1und1.de>

语法：ndpexhaust6接口destination-network [sourceip]

在目标网络中随机ping IP
node_query6 - 向目标发送ICMPv6节点查询请求
root @ kali：〜＃node_query6
node_query6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：node_query6接口目标

向目标发送ICMPv6节点查询请求并转储回复。
寄生虫6 - 这是IPv6的“ARP​​欺骗者”
root @ kali：〜＃寄生虫6
parasite6 v2.3（c）2013 van van Hauser / THC <vh@thc.org> www.thc.org

语法：parasite6 [-lRFHD] interface [fake-mac]

这是IPv6的“ARP​​欺骗者”，将所有本地流量重定向到您自己的
系统（或虚假的，如果假mac不存在）通过回答错误
邻居请求
选项-l循环并每5秒重新发送一次目标数据包。
选项-R也将尝试注入招标的目的地
NS安全旁路：-F片段，-H逐跳和-D大目标头
passive_discovery6 - 被动地嗅探网络并转储所有客户端的IPv6地址
root @ kali：〜＃passive_discovery6
passive_discovery6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：passive_discovery6 [-Ds] [-m maxhop] [-R prefix] interface [script]

选项：
 -D还要转储目标地址（不适用于-m）
 -s只打印地址，没有其他输出
 -m maxhop被转储的目标的最大跳数可能会消失。
             0表示仅限本地，最大限度是通常为5
 -R前缀将定义的前缀与链路本地前缀进行交换

被动嗅探网络并转储检测到的所有客户端的IPv6地址。
请注意，在切换的环境中，当您另外获得更好的结果
开始寄生虫6，但这会影响网络。
如果在接口后面指定了一个脚本名称，它将被调用
检测到ipv6地址为第一个，接口为第二个选项。
randicmp6 - 将所有ICMPv6类型和代码组合发送到目标
root @ kali：〜＃randicmp6
语法：randicmp6 [-s sourceip] interface destination [type [code]]

将所有ICMPv6类型和代码组合发送到目标。
选项-s设置源ipv6地址。
redir6 - 将路由插入victim-ip，将所有流量重定向到target-ip
root @ kali：〜＃redir6
redir6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：redir6 interface victim-ip target-ip original-router new-router [new-router-mac] [hop-limit]

将一条路径植入victim-ip，将所有流量重定向到目标ip
新ip。您必须知道将处理路由的路由器。
如果new-router-mac不存在，则会导致DOS。
如果目标的TTL不是64，则指定这是最后一个选项。
redirsniff6 - 将路由插入victim-ip，将所有流量重定向到destination-ip
root @ kali：〜＃redirsniff6
redirsniff6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：redirsniff6 interface victim-ip destination-ip original-router [new-router [new-router-mac]]

将路由插入victim-ip，将所有流量重定向到destination-ip
新路由器。这是通过该匹配流动的所有流量完成的
受害者 - >目标。您必须知道将处理路由的路由器。
如果新路由器/ -mac不存在，则会导致DOS。
您可以为victim-ip和/或destination-ip提供通配符（'*'）。
rsmurf6 - 蓝精灵受害者的本地网络
root @ kali：〜＃rsmurf6
rsmurf6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：rsmurf6 interface victim-ip

蓝精灵受害者的本地网络。注意：这取决于一个
实现错误，目前只在Linux上验证。
邪恶：“ff02 :: 1”作为受害者将完全DOS本地局域网
sendpees6 - 发送SEND邻居请求消息
root @ kali：〜＃sendpees6
sendpees6 by willdamn <willdamn@gmail.com>

用法：sendpees6 <inf> <key_length> <前缀> <victim>

发送SEND邻居请求消息，并使目标验证一个lota CGA和RSA签名
sendpeesmp6 - 发送SEND邻居请求消息
root @ kali：〜＃sendpeesmp6
原始发送者willdamn <willdamn@gmail.com>
修改sendpeesMP由Marcin Pohl <marcinpohl@gmail.com>
基于thc-ipv6的代码

用法：sendpeesmp6 <inferface> <key_length> <前缀> <victim>

发送SEND邻居请求消息，并使目标验证一个lota CGA和RSA签名
示例：sendpeesmp6 eth0 2048 fe80 :: fe80 :: 1
smurf6 - 用icmp echo回复smurf目标
root @ kali：〜＃smurf6
smurf6 v2.3（c）2013 by van Hauser / THC <vh@thc.org> www.thc.org

语法：smurf6 interface victim-ip [multicast-network-address]

用icmp回应回应目标。回应请求的目标是
本地全节点组播地址（如果未指定）
thcping6 - 制作您的特殊icmpv6 echo请求包
root @ kali：〜＃thcping6
thcping6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：thcping6 [-af] [-H o：s：v] [-D o：s：v] [-F dst] [-t ttl] [-c class] [-l label] [-d size] [-S端口| -U端口]接口src6 dst6 [srcmac [dstmac [data]]]

制作您的特殊icmpv6回应请求数据包。
您可以在src6，srcmac和dstmac中输入“x”作为自动值。
选项：
   - 将路由器警报选项添加到逐跳标头。
  -q使用quickstart选项添加一个逐跳标头。
  -E以ethertype IPv4的形式发送
  -H o：s：v添加具有特殊内容的逐跳标头
  -D o：s：v添加具有特殊内容的目的地标头
  -D“xxx”添加了一个大的目的地头，它会分片
  -f添加一个触发条纹标题
  -F ipv6address使用源路由到这个最终目的地
  -t ttl指定TTL（默认值：64）
  -c class指定一个类（0-4095）
  -l标签指定标签（0-1048575）
  -d data_size定义ping数据缓冲区的大小
  -S端口在定义的端口上使用TCP SYN数据包，而不是ping
  -U端口在定义的端口上使用UDP数据包，而不是ping
o：s：v syntax：option-no：size：value，value为十六进制，例如1：2：feab
返回-1错误或无回复，0正常回复或1错误回复。
thcsyn6 - 使用TCP-SYN数据包泛洪目标端口
root @ kali：〜＃thcsyn6
thcsyn6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：thcsyn6 [-AcDrRS] [-p port] [-s sourceip6]接口目标端口

选项：
 -A发送TCP-ACK数据包
 -S发送TCP-SYN-ACK数据包
 -r将您的/ 64前缀的源随机化
 -R将源完全随机化
 -s sourceip6使用此作为源ipv6地址
 -D随机化目的地（视为/ 64）
 -p端口使用固定源端口

用TCP-SYN数据包泛洪目标端口。如果你提供“x”作为端口，那么
是随机的
toobig6 - 在目标上植入指定的mtu
root @ kali：〜＃toobig6
toobig6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：toobig6 [-u] interface target-ip existing-ip mtu [hop-limit]

在目标上嵌入指定的mtu。
如果目标的TTL不是64，则指定为最后一个选项。
选项-u将发送TooBig，而不会从现有的ip发出欺骗的ping6。
trace6 - 一个基本但非常快的traceroute6程序
root @ kali：〜＃trace6
trace6 v2.3（c）2013由van Hauser / THC <vh@thc.org> www.thc.org

语法：trace6 [-abdt] [-s src6] interface targetaddress [port]

选项：
   - 将路由器警报选项插入一个逐跳标头。
  -D插入目标扩展头
  -E插入带有无效选项的目标扩展头
  -F插入一次性碎片头
  -b而不是ICMP6 Ping，使用TooBig（你不会看到目标）
  -B而不是ICMP6 Ping，使用PingReply（你不会看到目标）
  -d将IPv6地址解析为DNS。
  -t启用隧道检测
  -s src6指定源IPv6地址
最大跳数达到31

一个基本但非常快的traceroute6程序。
如果没有指定端口，则使用ICMP6 Ping请求，否则TCP SYN
数据包到指定的端口。选项D，E和F可以多次使用。
address6 Usage Example

Convert an IPv6 address to a MAC address and vice-versa:
root@kali:~# address6 fe80::76d4:35ff:fe4e:39c8
74:d4:35:4e:39:c8
root@kali:~# address6 74:d4:35:4e:39:c8
fe80::76d4:35ff:fe4e:39c8
alive6 Usage Example
root@kali:~# alive6 eth0
Alive: fd77:7c68:420a:1:426c:8fff:fe1b:cb90 [ICMP parameter problem]
Alive: fd77:7c68:420a:1:20c:29ff:fee5:5bf4 [ICMP echo-reply]
Alive: fd77:7c68:420a:1:75d9:4f39:a46a:6f83 [ICMP echo-reply]
Alive: fd77:7c68:420a:1:6912:8e80:e02f:1969 [ICMP echo-reply]
Alive: fd77:7c68:420a:1:201:6cff:fe6f:ddd1 [ICMP echo-reply]
detect-new-ip6 Usage Example
root@kali:~# detect-new-ip6 eth0
Started ICMP6 DAD detection (Press Control-C to end) ...
Detected new ip6 address: fe80::85d:9879:9251:853a
dnsdict6 Usage Example
root@kali:~# dnsdict6 example.com
Starting DNS enumeration work on example.com. ...
Starting enumerating example.com. - creating 8 threads for 798 words...
Estimated time to completion: 1 to 2 minutes
www.example.com. => 2606:2800:220:6d:26bf:1447:1097:aa7
```

原文链接:[http://tools.kali.org/information-gathering/thc-ipv6](http://tools.kali.org/information-gathering/thc-ipv6)
