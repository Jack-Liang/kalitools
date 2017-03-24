# Xplico软件包描述

Xplico的目标是获取网络流量中的应用信息数据。例如，从pcap文件中，Xplico可以提取每个电子邮件（POP、IMAP和SMTP协议）、HTTP、VoIP呼叫（SIP、MGCP、H323）、FTP、TFTP等内容。 Xplico不是网络协议分析器。

[Xplico首页](http://www.xplico.org/)| [Kali Xplico资源](http://git.kali.org/gitweb/?p=packages/xplico.git;a=summary)

- 作者：Gianluca Costa，Andre de Franceschi
- 许可证：GPLv2

## Xplico包含的工具
### xplico - 网络取证分析工具（NFAT）
```
root@kali:~# xplico -h
xplico v1.0.1
Internet Traffic Decoder (NFAT).
See http://www.xplico.org for more information.

Copyright 2007-2012 Gianluca Costa & Andrea de Franceschi and contributors.
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

This product includes GeoLite data created by MaxMind, available from http://www.maxmind.com/.

usage: xplico [-v] [-c <config_file>] [-h] [-g] [-l] [-i <prot>] -m <capute_module>
    -v 版本信息
    -c 配置文件
    -h 帮助信息
    -i 协议信息
    -g 显示协议的图形树
    -l 在屏幕中打印所有日志
    -m 捕获类型模块
    注意：参数必须遵守这个顺序！
```
## xplico用法示例

使用rltm模块（-m rltm）分析接口eth0（-i eth0）上的流量：
```
root@kali:~# xplico -m rltm -i eth0
xplico v1.0.1
Internet Traffic Decoder (NFAT).
See http://www.xplico.org for more information.

Copyright 2007-2012 Gianluca Costa & Andrea de Franceschi and contributors.
This is free software; see the source for copying conditions. There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

This product includes GeoLite data created by MaxMind, available from http://www.maxmind.com/.
Configuration file (/opt/xplico/cfg/xplico_cli.cfg) found!
GeoLiteCity.dat found!
pcapf: running: 0/0, subflow:0/0, tot pkt:1
pol: running: 0/0, subflow:0/0, tot pkt:0
eth: running: 0/0, subflow:0/0, tot pkt:1
pppoe: running: 0/0, subflow:0/0, tot pkt:0
ppp: running: 0/0, subflow:0/0, tot pkt:0
ip: running: 0/0, subflow:0/0, tot pkt:0
```

原文链接：[http://tools.kali.org/information-gathering/xplico](http://tools.kali.org/information-gathering/xplico)
