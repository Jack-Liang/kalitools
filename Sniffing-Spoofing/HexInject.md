# HexInject

## HexInject软件包介绍

HexInject是一个多功能包注入和嗅探工具，它为用户提供了一个基于命令行的框架来访问原始网络。它在开发之初就被设计为和其他基于命令行的工具一起使用，因此，它可以生成功能强大的shell脚本，以一种对用户完全透明的方式实现读取，拦截和修改网络流量。

源地址：http://hexinject.sourceforge.net/

[HexInject 主页](http://hexinject.sourceforge.net/) | [Kali HexInject 项目](http://git.kali.org/gitweb/?p=packages/hexinject.git;a=summary)

- 作者：Emanuele Acri

- 证书：BSD

## HexInject软件包中包含的工具
### hexinject - 十六进制包注入/嗅探工具

```
root@kali:~# hexinject -h
HexInject 1.5 [十六进制包注入/嗅探工具]
作者: Emanuele Acri <crossbower@gmail.com>

使用方法:
   hexinject <模式> <其他参数>

参数:
  -s 嗅探模式
  -p 注入模式
  -r 原始数据显示模式 (默认为16进制显示)
  -f <滤过器> 自定义pcap滤过器
  -i <设备> 指定要使用的网络设备
  -F <文件> 指定用于模拟设备的pcap文件 (仅限嗅探模式)
  -c <数量> 要抓取的包的数量
  -t <时间> 延时的毫秒数 (默认是100)
  -I 列出全部可用的网络设备

注入参数:
  -C 禁用自动数据包和校验
  -S 禁用自动分配数据包大小

网卡参数:
  -P 禁用多源模式
  -M 将无线网卡设为监听模式
     (实验性功能: 使用 airmon-ng 以替代...)

其他参数:
  -h 帮助界面
```

## prettypacket – 网路裸包反汇编器

```
root@kali:~# prettypacket -h
PrettyPacket 1.5 [网路裸包反汇编器]
作者: Emanuele Acri <crossbower@gmail.com>

用法:
    prettypacket [-x|-h]

参数:
    -x 按类型输出包样例以检查其结构
            (可用的类型: tcp, udp, icmp, igmp, arp, stp)
    -h  显示此帮助文档  
```

## hex2raw – 将输入流中的十六进制字串转换为输出流中的原始数据

```
root@kali:~# hex2raw -h
Hex2Raw 1.5 [将输入流中的十六进制字串转换为输出流中的原始数据]
作者: Emanuele Acri <crossbower@gmail.com>

用法:
    hex2raw [-r|-h]

Options:
    -r  反向转换 (原始数据转换为十六进制字串)
    -h  显示此帮助文档
```

## packets.tcl – 生成二进制包

```
root@kali:~# packets.tcl -h
Packets.tcl -- 以类似APD的格式生成指定的二进制包: http://wiki.hping.org/26

用法:
    packets.tcl 'APD 包描述'

示例包:

ethernet(dst=ff:ff:ff:ff:ee:ee,src=aa:aa:ee:ff:ff:ff,type=0x0800)+ip(ihl=5,ver=4,tos=0xc0,totlen=58,id=62912,fragoff=0,mf=0,df=0,rf=0,ttl=64,proto=1,cksum=0xe500,saddr=192.168.1.7,daddr=192.168.1.6)+icmp(type=3,code=3,unused=0)+data(str=aaaa)+udp(sport=33169,dport=10,len=10,cksum=0x94d6)+data(str=aaaa)+arp(htype=ethernet,ptype=ip,hsize=6,psize=4,op=request,shard=00:11:22:33:44:55,sproto=192.168.1.1,thard=22:22:22:22:22:22,tproto=10.0.0.1)

ethernet(dst=ff:ff:ff:ff:ff:ff,src=ff:ff:ff:ff:ff:ff,type=0x0800)+ip(ihl=5,ver=4,tos=00,totlen=30,id=60976,fragoff=0,mf=0,df=1,rf=0,ttl=64,proto=tcp,cksum=0x40c9,saddr=192.168.1.9,daddr=173.194.44.95)+tcp(sport=32857,dport=80,seq=1804471615,ack=0,ns=0,off=5,flags=s,win=62694,cksum=0xda46,urp=0)

ethernet(dst=ff:ff:ff:ff:ff:ff,src=ff:ff:ff:ff:ff:ff,type=0x0800)+ip(ihl=5,ver=4,tos=00,totlen=30,id=60976,fragoff=0,mf=0,df=1,rf=0,ttl=64,proto=tcp,cksum=0x40c9,saddr=192.168.1.9,daddr=173.194.44.95)+tcp(sport=32857,dport=80,seq=1804471615,ack=0,ns=0,off=8,flags=s,win=62694,cksum=0xda46,urp=0)+tcp.nop()+tcp.nop()+tcp.timestamp(val=54111314,ecr=1049055856)+data(str=f0a)
```

## hexinject 用法示例

以嗅探模式启动 **(-s)** ，使用 eth0 网路接口 **(-i eth0)**:

```
root@kali:~# hexinject -s -i eth0
FF FF FF FF FF FF 40 6C 8F 1B CB 90 08 00 45 00 00 31 E4 36 00 00 40 11 11 4E C0 A8 01 E8 C0 A8 01 FF D3 C6 7E 9C 00 1D B1 DA 4D 2D 53 45 41 52 43 48 20 2A 20 48 54 54 50 2F 31 2E 31 0D 0A
FF FF FF FF FF FF 40 6C 8F 1B CB 90 08 00 45 00 00 31 A1 63 00 00 40 11 54 21 C0 A8 01 E8 C0 A8 01 FF FF 69 7E 9E 00 1D 86 35 4D 2D 53 45 41 52 43 48 20 2A 20 48 54 54 50 2F 31 2E 31 0D 0A
FF FF FF FF FF FF 7C C3 A1 A4 B4 70 08 00 45 00 00 31 BF 94 00 00 40 11 35 FC C0 A8 01 DC C0 A8 01 FF E3 ED 7E 9C 00 1D A1 BF 4D 2D 53 45 41 52 43 48 20 2A 20 48 54 54 50 2F 31 2E 31 0D 0A
FF FF FF FF FF FF 7C C3 A1 A4 B4 70 08 00 45 00 00 31 2F DE 00 00 40 11 C5 B2 C0 A8 01 DC C0 A8 01 FF C5 16 7E 9E 00 1D C0 94 4D 2D 53 45 41 52 43 48 20 2A 20 48 54 54 50 2F 31 2E 31 0D 0A
```

## prettypacket 用法示例

输出UDP包的一个样例 **(-x udp)**:

```
root@kali:~# prettypacket -x udp

以太网包头:
 1C AF F7 6B 0E 4D        目标硬件地址
 AA 00 04 00 0A 04        源硬件地址
 08 00                    长度/类型

IP包头:
 45                       版本 / 包头长度
 00                       ToS / DFS
 00 3C                    总长度
 9B 23                    ID
 00 00                    标志 / 段位移
 40                       TTL
 11                       包协议
 70 BC                    和校验
 C0 A8 01 09              源地址
 D0 43 DC DC              目标地址

UDP包头:
 91 02                    源端口
 00 35                    目标端口
 00 28                    长度
 6F 0B                    和校验

负载或包尾:
 AE 9C 01 00 00 01 00 00 00 00 00 00 03 77 77 77 06 67 6F 6F 67 6C 65 03 63 6F
 6D 00 00 01 00 01
```

## hex2raw 用法示例

```
root@kali:~# hex2raw 
 FF 40 6C 8F 1B CB 90 08 00 45 00 00 31 E4 36 00 00 40 11 11 4E C0 A8 01 E8 C0 A8 01 FF D3 C6 7E 9C 00 1D B1 DA 4D 2D 53 45 41 52 43 48 20 2A 20 48 54 54 50 2F 31 2E 31 0D 0A
FF FF FF FF FF FF 40 6C 8F 1B CB 90 08 00 45 00 00 31 A1 63 00 00 40 11 54 21 C0 A8 01 E8 C0 A8 01 FF FF 69 7E 9E 00 1D 86 35 4D 2D 53 45 41 52 43 48 20 2A 20 48 54 54 50 2F 31 2E 31 0D 0A
������@lE1�c@T!�������i~��5M-SEARCH * HTTP/1.1
```

## packets.tcl 用法示例

```
root@kali:~# packets.tcl 'ethernet(dst=ff:ff:ff:ff:ee:ee,src=aa:aa:ee:ff:ff:ff,type=0x0800)+ip(ihl=5,ver=4,tos=0xc0,totlen=58,id=62912,fragoff=0,mf=0,df=0,rf=0,ttl=64,proto=1,cksum=0xe500,saddr=192.168.1.7,daddr=192.168.1.6)+icmp(type=3,code=3,unused=0)+data(str=aaaa)+udp(sport=33169,dport=10,len=10,cksum=0x94d6)+data(str=aaaa)+arp(htype=ethernet,ptype=ip,hsize=6,psize=4,op=request,shard=00:11:22:33:44:55,sproto=192.168.1.1,thard=22:22:22:22:22:22,tproto=10.0.0.1)' > packet-out
```
