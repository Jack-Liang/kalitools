# DNSChef包描述
DNSChef旨在为渗透测试人员和恶意软件分析师提供一个高度可配置的DNS代理。DNS代理（也称为“Fake DNS”）是用于应用程序
网络流量分析以及其他用途的工具。例如，DNS代理可以用于伪造对“badguy.com”的请求使其指向本地机器来终止或拦截，而不是指向Internet上的某个真实主机。
现有的一些DNS代理，大多只是简单地将所有DNS查询指向单个IP地址或仅实施初步过滤。DNSChef是作为渗透测试的一部分而开发的，这需要配置更灵活的系统。
因此，DNSChef是跨平台应用程序，基于广泛和专用域名列表，能够支持多个DNS记录类型，匹配域与通配符，代理不匹配域的真实响应，定义外部配置文件，
IPv6和许多其他功能。您可以在下面找到每个功能和参考用途的详细说明。在无法强制应用程序直接使用某些其他代理服务器的情况下，建议使用DNS代理。例
如，某些移动应用程序完全忽略OSHTTP代理设置。在这些情况下，使用DNS代理服务器（如DNSChef）将允许您欺骗该应用程序转发到所需目标的连接。

资料来源：http://thesprawl.org/projects/dnschef/ 

[DNSChef主页](http://thesprawl.org/projects/dnschef/)|[ Kali DNSChef Repo](http://git.kali.org/gitweb/?p=packages/dnschef.git;a=summary)

- **作者：iphelix**
- **许可证：GPLv3**
## dnschef包中包含的工具
### dnschef - 用于渗透测试的DNS代理


```代码
root @ kali：〜＃dnschef -h 
用法：dnschef.py [选项]：
        _                _          __
         | | version 0.1  | |        / _|
       __| |_ __  ___  ___| |__   ___| |_
      / _` | '_ \/ __|/ __| '_ \ / _ \  _|
     | (_| | | | \__ \ (__| | | |  __/ |
      \__,_|_| |_|___/\___|_| |_|\___|_|
                   iphelix@thesprawl.org


DNSChef旨在为渗透测试人员和恶意软件分析师提供一个高度可配置的DNS代理。它
能够精确配置哪些DNS回复修改或简单地代理与实际响应。为了利用这个工具，您必
须手动配置或中毒DNS服务器条目来指向DNSChef。该工具需要root权限才能运行。

选项：
  -h，--help显示此帮助消息和退出
  --fakeip = 192.168.1.100 
                        用于匹配DNS查询的IP地址。如果您在不指定域名
                        的情况下使用此参数，则所有查询都将被欺骗。如
                        果需要定义多个IP 地址，请考虑使用--file 参数。

  --fakedomains = thesprawl.org，google.com 
                        逗号分隔的域名列表，将被解析为-ip 参数中指定
                        的FAKE值。所有其他域名将被解析为其真实值。
 
  --truedomains = thesprawl.org，google.com 
                        以逗号分隔的域名列表，将被解析为其TRUE值。所
                        有其他域名将被解析为-ip 参数中指定的假值。

  --nameservers = 4.2.2.1,4.2.2.2                        
                        以代理请求使用的备用DNS服务器的逗号分隔列表。
                        从列表中随机选择的服务器将用于代理请求。默认
                        情况下，该工具使用Google' s公共DNS服务器8.8.8.8。
 
  --file = FILE
                        定义一个包含DOMAIN=IP配对规则（每行一对）DNS响应
                        列表的文件。例如：google=1.1.1.1将迫使所有查询
                        “google.com”解析为“1.1.1.1”。使用--file与其他
                        参数组合实现更具体的操作。注：从文件获取的数据将
                        优先于其他。
                        
                        
  --interface = 0.0.0.0
                        定义用于DNS侦听器的接口。例如，使用127.0.0.1
                        仅侦听来自环回设备的请求。
                        
  --tcp                 使用TCP DNS代理取代默认UDP。
  
  -q，--quiet           不显示标题。
```
### dnschef用法示例

```代码
root @ kali：〜＃dnschef 
          _                _          __  
         | | version 0.1  | |        / _| 
       __| |_ __  ___  ___| |__   ___| |_ 
      / _` | '_ \/ __|/ __| '_ \ / _ \  _|
     | (_| | | | \__ \ (__| | | |  __/ |  
      \__,_|_| |_|___/\___|_| |_|\___|_|  
                   iphelix@thesprawl.org  

[*] DNS Chef在接口：127.0.0.1上启动
[*]使用以下域名服务器：8.8.8.8 
[*]未指定参数，以完全代理模式运行
```

[原文链接](http://tools.kali.org/sniffingspoofing/dnschef)

