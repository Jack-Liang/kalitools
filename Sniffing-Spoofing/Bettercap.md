# Bettercap
**************
## Bettercap包描述
**************
Bettercap是一款适用于网络攻击和监控的瑞士军刀。这是一个用于网络捕获，分析和MIMT攻击的网络安全工具。

[Lynis 主页](https://www.bettercap.org/)

[Kali Bettercap仓库](https://git.kali.org/gitweb/?p=packages/bettercap.git;a=summary)

[资料来源](https://github.com/bettercap/bettercap)

作者：Bettercap dev team

许可：GPLv3
***************

### Bettercap包中包含的工具
Bettercap——用于网络攻击和监控的瑞士军刀。

```

root@kali:~# bettercap -h
Usage of bettercap:
  -autostart string
        逗号分隔的模块列表会自动启动 (默认 "events.stream, net.recon")
  -caplet string
        从此文件中读取命令并在交互式会话中执行他们
  -cpu-profile file
        写入cpu配置  
  -debug        
        打印调试信息
  -env-file string
        从选定的文件中加载环境变量, 设为空值去禁用持续维持的环境
  -eval string
        在交互式会话中，使用命令行设置变量，运行一个或者多个命令并使用;隔开
  -iface string
        绑定网络接口, 如果为空，接口会自动选定默认值
  -mem-profile file
        写入内存配置
  -no-colors
        禁用输出颜色效果
  -no-history
        禁用交互式会话历史记录文件
  -silent
        禁止输出（记录）所有非错误的日志
```

### bettercap用法示例

以静默模式扫描系统（-Q），并以cronjob格式（-cronjob）输出：

```
root@kali:~# bettercap 
bettercap v2.11 (type 'help' for a list of commands)

172.16.10.0/24 > 172.16.10.212  » [12:34:15] [endpoint.new] endpoint 172.16.10.254 detected as 00:50:56:01:33:70 (VMware, Inc.).
172.16.10.0/24 > 172.16.10.212  » help

           help MODULE : 如果没有模块名提供,则列出可用命令或者显示模块的特定帮助信息
                active : 显示活动模块的相关信息
                  quit : 关闭会话并退出
         sleep SECONDS : 休眠一段时间（休眠所给出的秒数）
              get NAME : 获取一个变量名的值
        set NAME VALUE : 设置一个变量名的值
  read VARIABLE PROMPT : 显示一个提示来询问用户输入，并将其保存在变量中
                 clear : 清空屏幕中的信息
        include CAPLET : 在当前会话中加载并运行CAPLET
             ! COMMAND : 执行shell命令并且将其输出到屏幕。
        alias MAC NAME : 给一个已知MAC地址的终端设定一个别名

模块：
      any.proxy > not running
       api.rest > not running
      arp.spoof > not running
      ble.recon > not running
        caplets > not running
    dhcp6.spoof > not running
      dns.spoof > not running
  events.stream > running
            gps > not running
     http.proxy > not running
    http.server > not running
    https.proxy > not running
    mac.changer > not running
   mysql.server > not running
      net.probe > not running
      net.recon > running
      net.sniff > not running
   packet.proxy > not running
       syn.scan > not running
      tcp.proxy > not running
         ticker > not running
         update > not running
           wifi > not running
            wol > not running

172.16.10.0/24 > 172.16.10.212  » net.show

+-----------------+--------------------+----------+-------------------------+---------+---------+------------+
|       IP        |        MAC         |  Name    |         Vendor          | Sent    | Recvd  | Last Seen  |
+-----------------+--------------------+----------+-------------------------+---------+---------+------------+
| 172.16.10.212   | 00:b0:52:af:4a:50  | eth0     | Atheros Communications  | 0 B     | 0 B     | 12:34:15   |
| 172.16.10.2     | 00:50:56:13:37:0a  | gateway  | VMware, Inc.            | 49 kB   | 20 kB   | 12:34:15   |
|                 |                    |          |                         |         |         |            |
| 172.16.10.254   | 00:50:56:01:33:70  |          | VMware, Inc.            | 2.4 kB  | 2.4 kB  | 12:35:15   |
+-----------------+--------------------+----------+-------------------------+---------+---------+------------+

↑ 0 B / ↓ 3.2 MB / 11354 pkts / 0 errs


```
