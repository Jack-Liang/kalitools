---
title: Sakis 3G
categories: Hardware Hacking
tags: [Sakis3G,Hardware Hacking,kali linux]
date: 2019-06-25 11:21:00
---
0x00 Sakis 3G介绍
-------------
Sakis3G是一个调整过的，即装即用的shell脚本，理论而言可以在任意调制解调器与运营商之间建立3G连接。它可以自动地配置好你的调制解调器或蓝牙模块，甚至可以检测运营商配置。在其他措施都失败之后，可以考虑使用这个工具。

~~Sakis3G主页~~ | [Kali上的Sakis3G软件库](http://git.kali.org/gitweb/?p=packages/sakis3g.git;a=summary)

- 作者: Sakis Dimopoulos
- 证书: GPLv2

0x01 包含的工具
----------------

##### sakis3g – Sakis 3G整合脚本

```
root@kali:~# sakis3g help
Sakis 3G 整合脚本 - 版本 0.2.0e
(c) Sakis Dimopoulos 2009, 2010 under GNU GPL v2


用法:
      sakis3g [指令] [开关] [变量]

Sakis3G是一个调整过的，即装即用的shell脚本，理论而言可以在任意调制解调器与运营商之间建立3G连接。

注意: 这个脚本正常工作需要root权限。如果不是以root权限运行的，它会自动尝试获取权限。

常用的命令有:
connect       - 尝试建立3G连接。
disconnect    - 终止全部正在活动的PPP连接。
toggle        - 尝试建立3G连接。如果已经连接，它会改为断开此连接。
reconnect     - 尝试建立3G连接。如果已经连接，它会先断开再尝试重新连接。
start         - 与connect指令相同。以init.d脚本形式调用。
stop          - 与disconnect指令相同。以init.d脚本形式调用。
reload        - 与reconnect指令相同。以init.d脚本形式调用。
force-reload  - 与reload指令相同。以init.d脚本形式调用。
restart       - 与reload指令相同。以init.d脚本形式调用。
desktop       - 为此脚本创建桌面快捷方式。
status        - 显示连接状态和返回值。若已连接，则返回值是0；若未连接，则返回值是6。
help          - 显示此页面并退出。
man           - 显示软件手册。

注意: 要获得更多信息请查阅软件手册或查看Sakis3G官方wiki，地址为http://wiki.sakis3g.org/
```

0x02 用法示例
----------------

`root@kali:~# sakis3g --interactive "connect"`