#cisco-torch软件包描述

思科Torch大规模扫描，指纹和利用工具是在下一版“黑客暴露的思科网络”上编写的，因为市场上提供的工具无法满足我们的需求。

使得Cisco-torch不同于类似工具的主要特性是大量使用forking在后台启动多个扫描进程，以实现最高的扫描效率。此外，如果需要，它同时使用应用层指纹的几种方法。我们想要快速发现运行Telnet，SSH，Web，NTP和SNMP服务的远程思科主机，并针对发现的服务启动字典攻击。

资料来源：http://www.hackingciscoexposed.com/?link=tools 
cisco-torch主页 | Kali cisco-torch Repo

作者：出生由Arhont团队
许可证：LGPL-2.1
cisco-torch包中包含的工具

cisco-torch - Cisco设备扫描器

root @ kali：〜＃cisco-torch 
使用配置文件torch.conf ... 
加载include和plugin ... 
 版本
用法：cisco-torch <options> <IP，hostname，network> 

或：cisco-torch <options> F <hostlist> 

可用选项：
-O <输出文件> 
-A所有指纹扫描类型组合
-t Cisco Telnetd扫描
-s Cisco SSHd扫描
-u Cisco SNMP扫描
-g Cisco配置或tftp文件下载
-n NTP指纹扫描
-j TFTP指纹扫描
-l <type> log-level 
        c critical（默认）
        v verbose 
        d debug 
-w Cisco Web服务器扫描
-z Cisco IOS HTTP授权漏洞扫描
-c具有SSL支持的Cisco Webserver扫描
-b密码字典攻击（与-s，-u，-c，-w ，-j或-t）
-V打印工具版本和退出
示例：cisco-torch -A 10.10.0.0/16 
        cisco-torch -s -b -F sshtocheck.txt 
        cisco-torch -w -z 10.10.0.0/ 16 
        cisco-torch -j -b -g -F tftptocheck.txt-j或-t） -V打印工具版本和退出示例：cisco-torch -A 10.10.0.0/16 cisco-torch -s -b -F sshtocheck.txt cisco-torch -w -z 10.10.0.0/16 cisco-torch -j -b -g -F tftptocheck.txt-j或-t） -V打印工具版本和退出示例：cisco-torch -A 10.10.0.0/16 cisco-torch -s -b -F sshtocheck.txt cisco-torch -w -z 10.10.0.0/16 cisco-torch -j -b -g -F tftptocheck.txt
cisco-torch用法示例“

针对目标IP地址（192.168.99.202）运行所有可用的扫描类型（-A ）：

root @ kali：〜＃cisco-torch -A 192.168.99.202 
使用配置文件torch.conf ... 
加载include和plugin ... 

################### ##########################################＃
Cisco Torch Mass Scanner 
＃我们需要它... 
＃＃http: 
//www.arhont.com/cisco-torch.pl＃######################### ###################################### 

目标列表包含1个主机
8853：检查192.168.99.202 ... 
找不到HUH db，应该在fingerprint.db中
跳过Telnet指纹
*通过SNMP找到的*** *** 
系统说明：Cisco互联网操作系统软件
IOS（tm）3600软件（C3640-IK9O3S-M ），版本12.3（22），发布软件（fc2） 
技术支持：http://www.cisco.com/techsupport 
版权所有（c）1986-2007由cisco系统公司
编译周一24-Jan-07 1 

Cisco-IOS网络服务器发现
 HTTP / 1.1 401未授权
日期：Tue，13 Apr 1993 00:57:07 GMT 
服务器：cisco-IOS 
接受范围：无
WWW验证：基本realm =“level_15_access” 

401未授权的


 WWW验证Web服务器发现
 HTTP / 1.1 401未授权
日期：Tue，13 Apr 1993 00:57:07 GMT 
服务器：cisco-IOS 
接受范围：无
WWW验证：基本realm =“level_15_access” 

401未授权


---> 
- 所有扫描完成。思科火炬质量扫描仪 - 
--->退出。
