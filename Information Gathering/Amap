#Amap包描述

Amap是pentester的第一个下一代扫描工具。它尝试识别应用程序，即使它们在不同于正常端口的端口上运行。
它还识别基于非ascii的应用程序。这是通过发送触发数据包，并在响应字符串列表中查找响应来实现的。

**资料来源：https://www.thc.org/thc-amap/ 

Amap主页(http://www.thc.org/thc-amap/) | Kali Amap Repo(http://git.kali.org/gitweb/?p=packages/amap.git;a=summary)

- 作者：van Hauser和DJ RevMoon

- 许可证：其他

##amap包中的工具

###pcrap - 将随机数据发送到UDP，TCP或SSL端口以禁止响应

oot @ kali：〜＃amapcrap 
amapcrap v5.4（c）2011 by van Hauser / THC＆lt; vh@thc.org> 

语法：amapcrap [-S] [-u] [-m 0ab] [-M min，max] [-n connections] [-N delay] [-w delay] [-e] [-v] TARGET PORT 

```
选项：
-S在TCP连接后使用SSL（不能与-u 
使用）-u使用UDP协议（默认值：TCP）（不能与-c一起使用）
-n连接最大连接数量（默认值：无限制）
-N连接之间的延迟延迟ms（默认值：0）
-w关闭端口之前的延迟延迟（默认值：250） - 
服务器响应时不停止
-v verbose mode 
-m 0ab send as random crap：0-nullbytes，a-字母+空格，b-二进制
-M最小值，最大值最小值和随机废话最大长度
目标端口目标（IP或DNS）和端口发送随机废话

此工具随机数据发送到一个无声的端口非法的响应，它可以
再用于amap中以供将来检测。它输出适当的amap 
appdefs定义。注意：默认情况下，所有模式都被激活（0：10％，a：40％，
b：50％）。模式'a'总是发送一行以
\ r \ n 结尾的字母和空格。访问我们的主页http://www.thc.org
##amap - 应用MAPper：pentester的下一代扫描工具
```
##amap用法示例

扫描192.168.1.15上的端口80。显示接收到的横幅（b），不显示关闭的端口（q），并使用详细输出（v）：
```
root @ kali：〜＃amap -bqv 192.168.1.15 80 
使用触发器文件/etc/amap/appdefs.trig ... loaded 30 triggers 
使用响应文件/etc/amap/appdefs.resp ... loaded 346响应
使用触发器文件/etc/amap/appdefs.rpc ...加载450个触发器

amap v5.4（www.thc.org/thc-amap）从2014-05-13 19:07:16开始 - 应用程序MAPPING模式

总任务数量纯连接模式下执行：23 
对192.168.1.15:80/tcp（由触发SSL）协议相匹配HTTP -旗帜：\ n \ N501方法未实现\ n \ n 
<H1>方法未实施</ H1> 
\ n 

来/index.html不支持。
\ n 

\ n 

<hr /> 

\ n 

<address> Apache / 2.2.22（Debian）Server at 12 
Protocol on 192.168.1.15:80/tcp（由trigger ssl）匹配http-apache-2 - banner：\ n \ n501未实现方法\ n \ n </ address> 
<h1>方法未实现</ h1> 
\ n 

不支持/index.html。
\ n 

\ n 

<hr /> 

\ n 

<address> Apache / 2.2.22（Debian）服务器在12 
等待19个连接上的超时... </ address> amap v5.4完成在2014-05-13 19： 07:22
```
