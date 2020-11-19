---
title: Miranda 
categories: Information Gathering
tags: [kali linux,information gathering,UPNP]
date: 2020-11-19 11:10:00
---

## Miranda包说明

Miranda 是一个基于 Python 的 UPNP （即插即用）的客户端应用，其旨在发现、查询和与 UPNP 型设备交互，特别是互联网网关设备（又称路由器）。它可用于审核网络上启用了 UPNP 设备是否存在漏洞。它的功能包括：

- 支持选项补全和命令历史记录的交互 Shell
- 被动和主动发现 UPNP 型设备
- 可自定义的搜索引擎查询（查询特定设备或服务） 
- 完全控制应用程序设置，比如 IP 地址、端口和消息头
- 简单枚举 UPNP 设备、服务、操作和变量
- 输入/输出状态变量与服务操作的关联
- 能够向 UPNP 服务/设备发送操作
- 能够将数据保存到文件中以便以后进行分析和协作
- 命令记录

Miranda建立在Linux系统上并用于Linux系统，并且已经在具有Python 2.5的Linux 2.6内核上进行了测试。但是，由于它是用Python编写的，因此大多数功能应可用于任何受Python支持的平台。Miranda已针对Linksys，D-Link，Belkin 和 ActionTec 等多家供应商的IGD（交互式图形设计系统）进行了测试。默认情况下，所有Python模块均已安装在Linux Mint 5（Ubuntu 8.04）测试系统上。

源码: https://code.google.com/p/mirandaupnptool/

[Miranda 主页](http://code.google.com/p/mirandaupnptool/) | [Kali Miranda Repo](https://gitlab.com/kalilinux/packages/miranda)

- 作者：克雷格·赫夫纳（Craig Heffner）
- 许可证：MIT

### Miranda 软件包中包含的工具

##### miranda – UPNP 管理员工具

```shell
root@kali:~# miranda -h

命令行用法: /usr/bin/miranda [选项]

  -s <结构文件>    从结构文件加载以前的主机数据
  -l <日志文件>    记录用户提供的命令到日志文件
  -i <接口>        指定要使用的接口的名称（仅Linux，需要root）
  -u     禁用 show-uniq-hosts-only 选项 
  -d     启用调试模式
  -v     启用详细模式
  -h     显示帮助
```

### miranda 用法示例

在接口 eth0 ***（-i eth0）*** 上启动，以详细模式 ***（-v）***，然后启动发现模式 ***（msearch）***：

```shell

root@kali:~# miranda -i eth0 -v

绑定到接口 eth0 ...

启用详细模式！
upnp> msearch

进入'upnp:rootdevice'的发现模式 , 按 Ctl+C 停止...

****************************************************************

来自192.168.1.230:80的SSDP（简单服务发现协议）通知消息
XML 文件位于 http://192.168.1.230:80/description.xml
设备正在运行 FreeRTOS/6.0.5, UPnP/1.0, IpBridge/0.1
```
