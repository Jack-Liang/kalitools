# WOL-E软件包描述

WOL-E是一套利用计算机“网络唤醒”（Wake on LAN--WOL）功能的工具，该功能现在在许多Apple电脑上默认启用。这些工具包括：
- 强制用MAC地址唤醒客户端
- 嗅探网络上的WOL请求并将其保存到磁盘
- 嗅探网络上的WOL密码并将其保存到磁盘
- 唤醒单个客户端（嗅探攻击）
- 扫描网络上启用WOL功能的Apple设备
- 向所有检测到的Apple客户端发送批量WOL请求

资料来源：[https://code.google.com/p/wol-e/](https://code.google.com/p/wol-e/)

[WOL-E首页](http://code.google.com/p/wol-e/)| [Kali WOL-E资源](http://git.kali.org/gitweb/?p=packages/wol-e.git;a=summary)

- 作者：Nathaniel Carew
- 许可证：GPLv3    

## WOL-E包含的工具
### wol-e - 网络唤醒浏览器
```
root@kali:~# wol-e -h

[*] WOL-E 1.0
[*] Wake on LAN Explorer - A collection a WOL tools.
[*] by Nathaniel Carew

    -m
        唤醒单个电脑。
        如果需要密码，请在上述命令的末尾使用-k 00:12:34:56:78:90。
        wol-e -m 00:12:34:56:78:90 -b 192.168.1.255 -p <端口> -k <密码>
        默认值：
        端口：9
        广播地址：255.255.255.255
        密码：空
        
    -s
        嗅探网络上的WOL请求和密码。
        所有捕获的WOL请求将显示在屏幕上并写入/usr/share/wol-e/WOLClients.txt。
        wol-e -s -i eth0

    -a
        强制WOL客户端开机。
        wol-e -a -p <端口>
        将希望强制开机的地址范围放在bfmac.lst文件中。
        它们应采用以下格式：
        00:12:34:56
        默认端口：9

    -f
        检测网络上启用WOL功能的Apple设备。
        检测到的Apple MAC地址将输出到屏幕，并写入/usr/share/wol-e/AppleTargets.txt。
        wol-e -f

    -fa
        尝试唤醒所有记录在/usr/share/wol-e/AppleTargets.txt中的Apple目标。
        这将向列表中的每个客户端发送一个WOL数据包，并告诉您尝试了多少客户端。
        wol-e -fa
```
## wol-e使用示例

检测联网的Apple设备（-f）：
```
root@kali:~# wol-e -f

    [*] WOL-E 1.0 [*]
    [*] Wake on LAN Explorer - Scan for Apple devices.

    [*] arping 192.168.1.0/24 on eth0
    [*] Apple device detected: de:ad:be:ef:46:32 192.168.1.12. saving to AppleTargets.txt
```    

原文链接：[http://tools.kali.org/information-gathering/wol-e](http://tools.kali.org/information-gathering/wol-e)
