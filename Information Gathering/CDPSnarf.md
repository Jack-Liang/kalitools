---
title: Kali Linux信息收集之CDPSnarf
categories: Information Gathering
tags: [kali linux,cdp,cdpsnarf,sniffing,information gathering,enumeration]
date: 2016-10-19 13:33:31
---
0x00 CDPSnarf介绍
-------------

CDPSnarf是专门用于从CDP包提取信息的网络嗅探器，它提供所有信息通过一个“show cdp neighbors detail”命令返回Cisco路由器信息，甚至更多信息。

其工作原理主要是利用Cisco的[CDP协议][1]，来发现连接Cisco设备的设备的相关信息（CDP协议中包含），包括IP地址、操作系统及其版本、路由信息等等。几乎所有的Cisco设备都支持CDP协议。实际上它就是个接受Cisco设备发送的CDP协议数据包的软件，然后通过解析数据包来得到设备的信息，协议包中的包含的信息可以参考下面的特性。

 - CDP广告之间的时间间隔
 - CDP协议的版本号
 - TTL
 - 设备的ID号
 - 软件版本
 - 平台版本
 - 地址信息
 - 端口号
 - 功能
 - 复合
 - 将输出保存成PCAP格式的文件
 - 从PCAP格式文件中读
 - Debugging 协议数据包
 - 用IPv4和IPv6的协议测试

工具来源：https://github.com/Zapotek/cdpsnarf

[CDPSnarf主页][2] | [Kali CDPSnarf Repo仓库][3]

 - 作者：Tasos “Zapotek” Laskos
 - 证书：GPLv2

0x01 CDPSnarf功能
---------------

cdpsnarf - 提取CDP包中信息的网络嗅探器

```shell
root@kali:~# cdpsnarf -h
CDPSnarf v0.1.6 [$Rev: 797 $] initiated.
   作者: Tasos "Zapotek" Laskos
           <tasos.laskos@gmail.com>
              <zapotek@segfault.gr>
   主页: http://github.com/Zapotek/cdpsnarf

cdpsnarf -i <dev> [-h] [-w savefile] [-r dumpfile] [-d]

    -i  定义嗅探接口
    -w  将数据包写入PCAP转储文件
    -r  从PCAP转储文件读取数据包
    -d  显示调试信息
    -h  显示帮助消息并退出
```

0x02 CDPSnarf用法示例
-----------------

在 eth0（-i）接口上扫描，并把结果写入到 test.pcap（-w）文件：
```shell
root@kali:~# cdpsnarf -i eth0 -w test.pcap
CDPSnarf v0.1.6 [$Rev: 797 $] initiated.
   Author: Tasos "Zapotek" Laskos
           <tasos.laskos@gmail.com>
              <zapotek@segfault.gr>
   Website: http://github.com/Zapotek/cdpsnarf

Reading packets from eth0.
Waiting for a CDP packet...
```


  [1]: https://en.wikipedia.org/wiki/Cisco_Discovery_Protocol
  [2]: https://github.com/Zapotek/cdpsnarf
  [3]: http://git.kali.org/gitweb/?p=packages/cdpsnarf.git;a=summary