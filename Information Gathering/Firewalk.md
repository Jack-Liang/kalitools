---
title: Firewalk
categories: Information Gathering
tags: [information gathering,recon,kali linux,firewalk]
date: 2016-10-24 13:52:51
---
0x00 Firewalk介绍
-------------

Firewalk是一个主动的侦察网络安全工具，试图确定给定的IP转发设备将通过哪些第4层协议。Firewalk通过发送具有比目标网关更大的TTL的TCP或UDP数据包来工作。如果网关允许流量，则它将将分组转发到它们将到期的下一跳，并且引出ICMP_TIME_EXCEEDED消息。如果网关主机不允许流量，它可能会丢弃在那层上的数据包，我们将看不到响应。

要获得正确的IP TTL，将导致过期的数据包超出网关，我们需要增加跳数。我们以跟踪traceroute工作的同样方式做，一旦我们有网关跳转计数（在那一点扫描被称为“绑定”），我们可以开始我们的扫描。

重要的是注意到不必达到最终目的地主机的事实，它只需要在扫描主机的网关的下游。

更多介绍：[Firewalk:高级路由跟踪工具(Linux)][1]

工具来源：http://packetfactory.openwall.net/projects/firewalk/


[Firewalk主页][2] | [Kali Firewalk Repo仓库][3]

 - 作者：Mike D. Schiffman, David Goldsmith

 - 证书：BSD

0x01 Firewalk功能
---------------

```shell
root@kali:~# firewalk -h
Firewalk 5.0 [gateway ACL scanner]
用法：firewalk [options] target_gateway metric
            [-d 0-65535] 要使用的目标端口（斜坡阶段）
            [-h] 程序帮助
            [-i device] 接口
            [-n] 不会将IP地址解析到主机名中
            [-p TCP|UDP] 协议
            [-r] 严格遵守RFC
            [-S x-y，z] 端口范围进行扫描
            [-s 0-65535] 源端口
            [-T 1-1000] 数据包读取超时（以毫秒为单位）
            [-t 1-25] IP生存时间
            [-v] 程序版本
            [-x 1-8] 预期向量
```

0x02 Firewalk用法示例
-----------------

```shell
root@kali:~# firewalk -S 8079-8081  -i eth0 -n -p TCP 192.168.1.1 192.168.0.1
Firewalk 5.0 [gateway ACL scanner]
Firewalk state initialization completed successfully.
TCP-based scan.
Ramping phase source port: 53, destination port: 33434
Hotfoot through 192.168.1.1 using 192.168.0.1 as a metric.
Ramping Phase:
 1 (TTL  1): expired [192.168.1.1]
Binding host reached.
Scan bound at 2 hops.
Scanning Phase:
port 8079: *no response*
port 8080: A! open (port not listen) [192.168.0.1]
port 8081: *no response*

Scan completed successfully.

Total packets sent:                4
Total packet errors:               0
Total packets caught               2
Total packets caught of interest   2
Total ports scanned                3
Total ports open:                  1
Total ports unknown:               0
```

0x02 提示
-----------------

新版Kali已移除Firewalk，如果你需要安装Firewalk可以使用以下命令：
```shell
root@kali:~# apt-get update
root@kali:~# apt-get install firewalk
```

  [1]: http://www.enet.com.cn/article/2011/0411/A20110411847512.shtml
  [2]: http://packetfactory.openwall.net/projects/firewalk/
  [3]: http://git.kali.org/gitweb/?p=packages/firewalk.git;a=summary