##bing-ip2hosts软件包描述

Bing.com是微软拥有的以前称为MSN搜索和实时搜索的搜索引擎。它具有搜索托管在特定IP地址上的网站的独特功能。Bing-ip2hosts使用此功能枚举Bing已为特定IP地址编入索引的所有主机名。这种技术被认为是在渗透测试的侦察阶段的最佳实践，以便发现更大的潜在攻击面。Bing-ip2hosts是用Bash的Bash脚本语言编写的。这使用移动界面，不需要API密钥。

资料来源：http://www.morningstarsecurity.com/research/bing-ip2hosts 
bing-ip2hosts主页(http://www.morningstarsecurity.com/research/bing-ip2hosts/) | Kali bing-ip2hosts Repo(http://git.kali.org/gitweb/?p=packages/bing-ip2hosts.git;a=summary)

- 作者：Andrew Horton
- 许可证：GPLv3
##bing-ip2hosts包中包含的工具

###bing-ip2hosts - 使用bing.com枚举IP的主机名

```
root @ kali：〜＃bing-ip2hosts 
bing-ip2hosts（o.4）作者：Andrew Horton aka urbanadventurer 
主页：http://www.morningstarsecurity.com/research/bing-ip2hosts 

用于网络智能和vhosts攻击面映射
渗透测试。查找与目标共享IP地址
的主机名，可以是主机名或IP地址。这利用Microsoft 
Bing.com通过IP地址搜索的能力，例如“IP：210.48.71.196”。

用法：/ usr / bin / bing-ip2hosts [选项]＆lt; IP | hostname＆gt; 

选项是：
-n关闭进度指示器动画
-t 

<dir>使用此目录而不是/ tmp。该目录必须存在。
-i可选CSV输出。在每行上输出IP和主机名，以逗号分隔。
-p可选http：//前缀输出。用于在shell中右键单击。
</ dir>
```
bing-ip2hosts用法示例

```
root @ kali：〜＃bing-ip2hosts -p microsoft.com 
[65.55.58.201 | 刮擦1 | 找到0 | /] 
http://microsoft.com 
http://research.microsoft.com 
http://www.answers.microsoft.com 
http://www.microsoft.com 
http://www.msdn.microsoft.com
```

```
root @ kali：〜＃bing-ip2hosts -p 173.194.33.80 
[173.194.33.80 | 刮刮60-69 | 找到41 | | ] | /] 
http://asia.google.com 
http://desktop.google.com 
http://ejabat.google.com 
http://google.netscape.com 
http://partner-client.google.com 
http ：//picasa.google.com
```
