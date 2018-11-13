---
title: ace-voip
categories: Information Gathering
tags: [sniffing,information gathering,ace-voip,enumeration,kali linux,cdp]
date: 2016-10-18 15:22:00
---
# ace-voip包描述
ACE（自动公司枚举器）是一个简单而强大的VoIP公司目录枚举工具，模拟IP电话的行为，以便下载给定手机可在其屏幕界面上显示的名称和扩展条目。 以同样的方式，VoIP硬件电话的“企业目录”功能使用户能够通过他们的VoIP手机通过名称轻松拨号，ACE的开发是来自一个针对名字企业目录实现“VoIP Hopper”自动化VoIP攻击的研究想法。 这个概念意味着将来可以基于用户的名字对用户进行攻击，而不是针对随机RTP音频流或IP地址定位VoIP流量。ACE通过使用DHCP，TFTP和HTTP工作，以便下载VoIP公司目录。 然后将目录输出到文本文件，该文本文件可用作其他VoIP评估工具的输入。

**资料来源：** http://ucsniff.sourceforge.net/ace.html 

[ace-voip主页](http://ucsniff.sourceforge.net/ace.html) | [Kali ace-voip Repo](http://git.kali.org/gitweb/?p=packages/ace-voip.git;a=summary)

- 作者：Sipera VIPER实验室
- 许可证：GPLv3
## ace-voip包中包含的工具
### ace - 一个简单的VoIP企业目录枚举工具

```
root@kali:~# ace
ACE v1.10：自动企业（数据）枚举器
用法：ace [-i 接口] [-m 物理地址] [-t tftp服务器ip地址 | -c cdp模式 | -v 语音vlan id | -r vlan接口 | -d详情模式] 

-i（必选）嗅探/发送报文的接口
-m（必选）受害者的IP地址IP电话
-t（可选）tftp服务器ip地址
-c（可选）0 CDP嗅探模式，1 CDP欺骗模式 
-v（可选）输入语音 vlan ID 
-r（可选）删除VLAN接口
-d（可选）详情 | 调试模式

示例用法：
使用-m选项需要提供的IP电话的MAC地址
用法：ace -t -m 

通过DHCP选项150（-m）自动发现TFTP服务器IP的模式
示例: ace -i eth0 -m 00:1E:F7:28:9C:8E

指定TFTP服务器的IP地址的模式
示例: ace -i eth0 -t 192.168.10.150 -m 00:1E:F7:28:9C:8e

指定语音vlan id的模式
示例: ace -i eth0 -v 96 -m 00:1E:F7:28:9C:8E

详情模式
示例: ace -i eth0 -v 96 -m 00:1E:F7:28:9C:8E -d

移除vlan接口的模式
示例: ace -r eth0.96

在CDP的侦听模式下自动发现语音vlan ID
示例: ace -i eth0 -c 0 -m 00:1E:F7:28:9C:8E


在CDP的欺骗模式下自动发现语音vlan ID的模式
示例: ace -i eth0 -c 1 -m 00:1E:F7:28:9C:8E

```
## ace-voip用法示例

```
root@kali:~# 即将推出
```

---
译者：Jack，校对：Jack, Sunnyelf

原文链接https://tools.kali.org/information-gathering/ace-voip
