# Wireshark软件包描述

Wireshark是世界上首屈一指的网络协议分析器，它可以让您在微观层面看到网络上发生的情况，事实上（常常是法律上）它是许多行业和教育机构的标准工具。感谢全球网络专家的贡献，Wireshark蓬勃发展。它是1998年开始的一个项目的延续。

Wireshark具有丰富的功能集，包括以下内容：

- 深入检查数百种协议，并且还一直在加入更多的内容
- 实时捕获和离线分析
- 标准的三窗格数据包浏览器
- 支持多平台：可以运行于Windows、Linux、OS X、Solaris、FreeBSD、NetBSD等系统
- 捕获的网络数据可以通过GUI或终端模式的TShark工具浏览
- 业界最强大的显示过滤器
- 丰富的VoIP分析
- 使用gzip压缩的捕获文件可以迅速解压缩
- 实时数据可以从以太网、IEEE 802.11、PPP/HDLC、ATM、蓝牙、USB、令牌环、帧中继、FDDI等（根据您的平台）读取，
- 着色规则可以应用于分组列表，以进行快速、直观的分析
- 输出可以导出为XML、PostScript®、CSV或纯文本
- 许多协议的解密支持，包括IPsec、ISAKMP、Kerberos、SNMPv3、SSL/TLS、WEP和WPA/WPA2
- 读/写许多不同格式的捕获文件：tcpdump（libpcap）、Pcap NG、Catapult DCT2000、Cisco Secure IDS iplog、Microsoft网络监视器、Network General Sniffer®（压缩和未压缩）、Sniffer®Pro，以及NetXray®、Network Instruments Observer、NetScreen snoop、Novell LANalyzer、RADCOM WAN/LAN Analyzer、Shomiti/Finisar Surveyor、Tektronix K12xx、Visual Networks Visual UpTime、WildPackets EtherPeek/TokenPeek/AiroPeek，等等

资料来源：http://www.wireshark.org/about.html

[Wireshark主页](http://www.wireshark.org/)| [Kali Wireshark资源](http://git.kali.org/gitweb/?p=packages/wireshark.git;a=summary)

- 作者：Gerald Combs和贡献者
- 许可证：GPLv2

## Wireshark包含的工具
### wireshark - 网络流量分析器 - GTK+版本
```
root@kali:~# wireshark -h
Wireshark 1.10.2 (SVN Rev 51934 from /trunk-1.10)
Interactively dump and analyze network traffic.
See http://www.wireshark.org for more information.

Copyright 1998-2013 Gerald Combs <gerald@wireshark.org> and contributors.
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

用法：wireshark [options] ... [<infile>]

捕获接口：
  -i <interface>        接口的名称或序号（默认：第一个非loopback接口）
  -f <capture filter>   libpcap语法格式的包过滤器
  -s <snaplen>          数据包快照长度（默认：65535）
  -p                    不在混杂模式下捕获
  -k                    立即开始捕获（默认：不捕获）
  -S                    当有新数据包被捕获时，更新数据包显示
  -l                    当使用-S选项时打开自动滚动
  -I                    如果可用，在监听模式下捕获
  -B <buffer size>      内核缓冲区大小（默认：2MB）
  -y <link type>        链接层类型（默认：第一个适当的类型）
  -D                    打印接口列表并退出
  -L                    打印接口的链接层类型列表并退出

捕获停止条件：
  -c <packet count>     在n个包之后停止（默认：无限制）
  -a <autostop cond.> ... duration：NUM - NUM秒后停止
                          filesize：NUM - 在NUM KB后停止此文件
                             files：NUM - NUM个文件后停止

捕获输出：
  -b <ringbuffer opt> ... duration：NUM - NUM秒后切换到下一个文件
                          filesize：NUM - 在NUM KB后切换到下一个文件
                             files：NUM - ringbuffer：NUM个文件后替换

输入文件：
  -r <infile>           设置读取的文件名（不支持管道或标准输入！）

处理：
  -R <read filter>      Wireshark语法格式的包过滤器
  -n                    禁用所有名称解析（默认：全部启用）
  -N <name resolve flags> 启用特定的名称解析：“mntC”

用户界面：
  -C <config profile>   用指定的配置文件启动
  -Y <display filter>   用给定的显示过滤器启动
  -g <packet number>    在“-r”之后转到指定的包号
  -J <jump filter>      跳转到第一个匹配（显示）过滤器的数据包                           
  -j                    在“-J”之后向后搜索匹配的包
  -m <font>             设置大多数文字使用的字体名称
  -t a|ad|d|dd|e|r|u|ud 时间戳的输出格式（默认：r：相对首个包的时间）
  -u s|hms              秒的输出格式（默认：s：秒）
  -X <key>：<value>     扩展选项，详见手册页
  -z <statistics>       显示各种统计信息，详见手册页

输出：
  -w <outfile|->        设置输出文件名（或'-'代表标准输出）

杂项：
  -h                    显示此帮助并退出
  -v                    显示版本信息并退出
  -P <key>：<path>      persconf：path - 个人配置文件
                        persdata：path - 个人数据文件
  -o <name>：<value> ...覆盖首选项或最近的设置
  -K <keytab>           用于kerberos解密的keytab文件
  --display=DISPLAY     使用的X display
```  
### tshark - 网络流量分析器 - 控制台版本
```
root@kali:~# tshark -h
TShark 1.10.2 (SVN Rev 51934 from /trunk-1.10)
Dump and analyze network traffic.
See http://www.wireshark.org for more information.

Copyright 1998-2013 Gerald Combs <gerald@wireshark.org> and contributors.
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

用法：tshark [options] ...

捕获界面：
  -i <interface>        接口的名称或序号（默认：第一个非loopback接口）
  -f <capture filter>   libpcap语法格式的包过滤器
  -s <snaplen>          数据包快照长度（默认：65535）
  -p                    不在混杂模式下捕获
  -I                    如果可用，在监听模式下捕获
  -B <buffer size>      内核缓冲区大小（默认：2MB）
  -y <link type>        链接层类型（默认：第一个适当的类型）
  -D                    打印接口列表并退出
  -L                    打印接口的链接层类型列表并退出

捕获停止条件：
  -c <packet count>     在n个包之后停止（默认：无限制）
  -a <autostop cond.> ... duration：NUM - NUM秒后停止
                          filesize：NUM - 在NUM KB后停止此文件
                             files：NUM - NUM个文件后停止

捕获输出：
  -b <ringbuffer opt> ... duration：NUM - NUM秒后切换到下一个文件
                          filesize：NUM - 在NUM KB后切换到下一个文件
                             files：NUM - ringbuffer：NUM个文件后替换

输入文件：
  -r <infile>           设置读取的文件名（不支持管道或标准输入！）

处理：
  -2                    进行两阶段分析
  -R <read filter>      Wireshark语法格式的包过滤器
  -Y <display filter>   Wireshark语法格式的包显示过滤器
  -n                    禁用所有名称解析（默认：全部启用）
  -N <name resolve flags> 启用特定的名称解析：“mntC”
  -d <layer_type> == <selector>，<decode_as_protocol> ...
                        “Decode AS”，详见手册页
                        示例：tcp.port == 8888，http
  -H <hosts file>       从hosts文件读取条目列表，然后写入捕获文件。（隐含-W n选项）

输出：
  -w <outfile|->        数据包写入pcap格式的文件“outfile”（或'-'代表标准输出）
  -C <config profile>   用指定的配置文件启动
  -F <output file type> 设置输出文件类型，默认为pcapng
                        一个空的“-F”选项将列出文件类型
  -V                    添加输出到数据包树（包详细信息）
  -O <protocols>        只显示这些协议的数据包详细信息，协议用逗号分隔
  -P                    即使写入文件也打印数据包摘要
  -S <separator>        数据包之间打印的行分隔符
  -x                    添加十六进制和ASCII转储输出（数据包字节）
  -T pdml|ps|psml|text|fields
                        文本输出格式（默认：文本）
  -e <field>            指定打印字段，如果设置了-Tfields选项（例如tcp.port、col.Info）;
                        可以重复此选项以打印多个字段
  -E<fieldsoption>=<value>  设置输出选项，如果选择了-Tfields：
     header=y|n             切换是否输出首部
     separator=/t|/s|<char> 选择跳格键、空格、可打印字符作为分隔符
     occurrence=f|l|a       打印每个字段的第一个、最后一个或所有的出现
     aggregator=,|/s|<char> 选择逗号、空格、可打印字符作为聚合符
     quote=d|s|n            选择双引号、单引号、无引号值
  -t a|ad|d|dd|e|r|u|ud 时间戳的输出格式（默认：r：相对首个包的时间）
  -u s|hms              秒的输出格式（默认：s：秒）
  -l                    每个数据包后刷新标准输出
  -q                    静默标准输出（例如统计信息时）
  -Q                    只输出错误信息（比-q更安静）
  -g                    启用输出文件的用户组读权限
  -W n                  如果支持，在文件中保存额外的信息。
                        n=写入网络地址解析信息
  -X <key>：<value>     扩展选项，详见手册页
  -z <statistics>       显示各种统计信息，详见手册页

杂项：
  -h                    显示此帮助并退出
  -v                    显示版本信息并退出
  -o <name>：<value> ...覆盖首选项设置
  -G [report]           转储几个可用报告之一并退出
                        默认report="fields"
                        用"-G ?"获取更多帮助
```
## tshark使用示例
```
root@kali:~# tshark -f "tcp port 80" -i eth0
```
## wireshark使用示例
```
root@kali:~# wireshark
```
![Image](http://tools.kali.org/wp-content/uploads/2014/02/wireshark.png)

原文链接：[http://tools.kali.org/information-gathering/wireshark](http://tools.kali.org/information-gathering/wireshark)
