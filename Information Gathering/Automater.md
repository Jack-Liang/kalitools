#自动机软件包描述

Automater是一个URL /域，IP地址和Md5哈希OSINT工具，旨在使分析过程更容易为入侵分析师。给定目标（URL，IP或HASH）或一个完整的目标文件Automater将返回来自如下来源的相关结果：IPvoid.com，Robtex.com，Fortiguard.com，unshorten.me，Urlvoid.com，Labs。 alienvault.com，ThreatExpert，VxVault和VirusTotal。

**资料来源**：http://www.tekdefense.com/automater/

Automater首页(http://www.tekdefense.com/automater/) | 卡利自动机(http://git.kali.org/gitweb/?p=packages/automater.git;a=summary)

- 作者：TekDefense.com

- 许可证：其他

##自动机软件包中包含的工具

###automater - IP和URL分析工具

```
root @ kali：〜＃automater -h 
用法：Automater.py [-h] [-o OUTPUT] [-w WEB] [-c CSV] [-d DELAY] [-s SOURCE] 
[--p] [ - -proxy PROXY] [-a USERAGENT] 
目标

IP，URL和Hash被动分析工具

位置参数：
target列出一个IP地址（接受CIDR或短划线符号），
URL或哈希以查询或传递
包含IP地址的文件的文件名信息，URL或哈希来查询每个
以换行符分隔。

可选参数：
-h，--help显示此帮助消息并退出
-o OUTPUT，-- 
output OUTPUT 此选项将结果输出到文件。
-w WEB，--web WEB此选项将结果输出到HTML文件。
-c CSV，--csv CSV此选项将结果输出到CSV文件。
-d DELAY，-​​- 
delay DELAY 这将会将延迟更改为输入的秒数。
默认值为2. 
-s SOURCE，-- source SOURCE 
此选项将仅针对
特定源引擎运行目标以拉取关联的域。
选项
在XML配置文件中的site 元素的name属性中定义
--p，--post此选项指示程序将信息发布到
允许发布的站点。默认情况下，程序
不会发布到需要发布信息的网站。
--proxy PROXY此选项将设置要使用的代理（例如 ，proxy.example.com : 
8080）
-a USERAGENT，--useragent USERAGENT 
此选项允许用户设置
正在使用的Web服务器看到的用户代理。默认情况下，user- 
agent设置为Automater / version
```
##automater用法示例

使用robtex作为源（-s）扫描有关IP地址50.116.53.73的信息：
```

root @ kali：〜＃automater -s robtex 50.116.53.73 
[*]检查http://api.tekdefense.com/robtex/rob.php?q=50.116.53.73 

____________________找到的结果：50.116.53.73 ____________________ 
[+]来自Robtex.com的记录：www.kali.org
```
