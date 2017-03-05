braa包装说明

Braa是一个质量snmp扫描仪。这种工具的预期用途当然是使SNMP查询 - 但不同于snmpget或来自net-snmp的snmpwalk，它能够在单个进程中同时查询几十或几百个主机。因此，它消耗非常少的系统资源，并且扫描非常快。

Braa实现了它的OWN snmp栈，所以它不需要任何SNMP库，如net-snmp。实现很脏，只支持几种数据类型，在任何情况下都不能说“符合标准”！它的设计是快速的，它是快速。因为这个原因（好吧，也是因为我的懒惰），在braa中没有ASN.1解析器 - 你知道OID的数值（例如.1.3.6.1.2.1.1.5.0而不是系统.sysName.0）。

资料来源：braa自述

[braa首页](http://s-tech.elsat.net.pl/) | [Kali braa回购](http://git.kali.org/gitweb/?p=packages/braa.git;a=summary)

- 作者：Mateusz'mteg'Golicz
- 许可证：GPLv2

##工具包括在braa包

###braa - 大规模SNMP扫描器

```
root @ kali：〜＃braa -h 
braa 0.81 - Mateusz'mteg'Golicz <mtg@elsat.net.pl>，2003 - 2006 
用法：braa [options] [query1] [query2] ... 
  -h显示此帮助。
  -2声称是SNMP2C代理。
  -v执行所有查询后显示简要摘要。
  -x Hexdump octet-strings 
  -t <s>等待秒以获取响应。
  -d <s>发送每个数据包后等待微秒。
  -p <s>在后续遍之间等待毫秒。
  -f <file>从文件<file>加载查询（逐行）。
  -a <time>在<time>秒后退出，独立于发生什么。
  -r <rc>重试计数（默认值：3）。

查询格式为：
  GET：[社区@] iprange [：端口]：OID [/ ID] 
  WALK：[社区@] iprange [：端口]：OID * [/ I D] 
  SET：[社区@] iprange [：端口] ：oid = value [/ id] 

示例：
         public@10.253.101.1：161：.1.3.6。* 
         10.253.101.1-10.253.101.255：.1.3.6.1.2.1.1.4.0 = sme 
         10.253.101.1:.1.3 .6.1.2.1.1.1.0 / description 

也可以一次指定多个查询：
         10.253.101.1-10.253.101.255：.1.3.6.1.2.1.1.4.0 = sme，.1.3.6。* 
         （Will设置.1.3.6.1.2.1.1.4.0为'me'，并从.1.3.6开始步行）


SET查询的值必须用一个指定值类型的字符作为前缀：
  i is INTEGER 
  a is IPADDRESS 
  s is OCTET STRING 
  o是OBJECT IDENTIFIER 
如果缺少类型说明符，则会自动检测值类型
```
##braa用法示例

使用public的community字符串在192.168.1.215上运行 SNMP树，查询.1.3.6下的所有OID ：

```
root @ kali：〜＃braa public@192.168.1.215：.1.3.6。* 
192.168.1.215:122ms:.1.3.6.1.2.1.1.1.0:Linux redhat.biz.local 2.4.20-8＃1 Thu 3月13日17:54:28 EST 2003 i686 
192.168.1.215:143ms:.1.3.6.1.2.1.1.2.0:.1.3.6.1.4.1.8072.3.2.10 
192.168.1.215:122ms:.1.3.6.1.2.1。 1.3.0：4051218219 
192.168.1.215:122ms:.1.3.6.1.2.1.1.4.0:Root <root @ localhost>（配置
/etc/snmp/snmp.local.conf）192.168.1.215:143ms:.1.3。 6.1.2.1.1.5.0：redhat.biz.local
```
