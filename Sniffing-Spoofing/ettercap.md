# ettercap
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
（ettercap的用法）
  -autostart string
        逗号分隔的模块列表会自动启动 (默认 "events.stream, net.recon")
  -caplet string
        从此文件中读取命令并在交互式会话中执行他们
  -cpu-profile file
        写入cpu配置  
-debug        
打印调试信息
  -env-file string
        从找到的这个文件中加载环境变量, 设为空值去禁用持续维持的环境
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

bettercap用法示例

以静默模式扫描系统（-Q），并以cronjob格式（-cronjob）输出：


root@kali:~# bettercap 
bettercap v2.11 (type 'help' for a list of commands)

172.16.10.0/24 > 172.16.10.212  » [12:34:15] [endpoint.new] endpoint 172.16.10.254 detected as 00:50:56:01:33:70 (VMware, Inc.).
172.16.10.0/24 > 172.16.10.212  » help

           help MODULE :如果没有模块名提供,则列出可用命令或者显示模块的特定帮助信息
                active : 显示活动模块的相关信息
                  quit : 关闭会话并退出
         sleep SECONDS : 休眠一段时间（休眠所给出的秒数）
              get NAME : 得到一个变量名的值
        set NAME VALUE : 设置一个变量名的值
  read VARIABLE PROMPT : 显示一个提示来询问用户输入，并将其保存在变量中
                 clear : 清空屏幕中的信息
        include CAPLET : 在当前会话中加载并运行CAPLET
             ! COMMAND : 执行shell命令并且将其打印输出。
        alias MAC NAME : 给一个已知（已经查到的）MAC地址的终端设定一个别名

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




*****************

### man手册的一些参数

```
root@kali:~# ettercap

ettercap 0.8.2 copyright 2001-2015 Ettercap Development Team

Please select an User Interface

root@kali:~# ettercap -h

ettercap 0.8.2 copyright 2001-2015 Ettercap Development Team


Usage: ettercap [OPTIONS] [TARGET1] [TARGET2]

TARGET is in the format MAC/IP/IPv6/PORTs (see the man for further detail)

嗅探和攻击选项:
  -M, --mitm <METHOD:ARGS>    实施一次mitm 攻击
  -o, --only-mitm             不进行嗅探，只实施一次mitm攻击
  -b, --broadcast             嗅探进行转播的数据包
  -B, --bridge <IFACE>        使用桥接嗅探 (需要两个接口（端口）)
  -p, --nopromisc             不将接口（端口）置于混杂模式
  -S, --nosslmitm             不伪造SSL证书。
  -u, --unoffensive           不转发数据包
  -r, --read <file>           从pcap文件中读取数据
  -f, --pcapfilter <string>   设置pcap过滤器
  -R, --reversed              使用反向目标选择（选择排除在外的目标）
  -t, --proto <proto>         只嗅探 proto (默认嗅探全部proto)
      --certificate <file>    用于SSL MiTM的证书
      --private-key <file>    用于 SSL MiTM的私钥文件

用户界面类型:
  -T, --text                  仅在GUI界面显示文本
       -q, --quiet            不显示包内容（类似于静默状态，但是只是不在界面显示）
       -s, --script <CMD>    将指定命令发送到GUI
  -C, --curses                使用图形模式
  -D, --daemon                后台模式
  -G, --gtk                    使用 GTK+ GUI

Logging options:
  -w, --write <file>           将嗅探数据写入pcap文件
  -L, --log <logfile>          将所有流量记录到指定文件中
  -l, --log-info <logfile>    和-L相似，但是只记录收集到的用户名和密码（被动嗅探）
  -m, --log-msg <logfile>     将所有消息记录到指定文件中
  -c, --compress                使用gzip格式压缩日志文件

可视化选项:
  -d, --dns                      将ip地址解析为主机名
  -V, --visual <format>       设定可视化格式
  -e, --regex <regex>         仅显示与此正则表达式匹配的数据包
  -E, --ext-headers           打印每个pck数据包的扩展头
  -Q, --superquiet            不显示用户名和密码（静默模式）

LUA options:
      --lua-script <script1>,[<script2>,...]     逗号分隔 LUA 脚本
      --lua-args n1=v1,[n2=v2,...]                 以逗号分隔的LUA脚本参数

General options:
  -i, --iface <iface>         使用这个网络接口
  -I, --liface                  显示所有网络接口
  -Y, --secondary <ifaces>    备用网卡接口列表
  -n, --netmask <netmask>     在接口上强制使用本地指定的子网掩码
  -A, --address <address>     在接口上强制使用本地指定的地址
  -P, --plugin <plugin>       启动这个指定的 plugin
  -F, --filter <file>         加载过滤器 
  -z, --silent                不进行arp毒化和主机扫描
  -6, --ip6scan               发送ICMPv6探针以发现链路上的IPv6节点
  -j, --load-hosts <file>     从某文件加载主机列表
  -k, --save-hosts <file>     保存主机列表到某文件 
  -W, --wifi-key <wkey>       使用密钥解密wifi数据包 (wep 或者 wpa)
  -a, --config <config>       使用备用配置文件
标准选项:
  -v, --version               打印版本并退出
  -h, --help                  显示帮助

```
