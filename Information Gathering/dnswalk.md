---
title: dnswalk
categories: Information Gathering
tags: [dnswalk,information gathering,recon,dns,kali linux]
date: 2016-10-21 10:07:46
---

0x00 dnswalk介绍
-------------

dnswalk是一个DNS调试器，它执行指定域的传送，并以多种方式检查数据库内部一致性以及准确性。

工具来源：http://sourceforge.net/projects/dnswalk/

[dnstracer主页][1] | [Kali dnstracer Repo仓库][2]

 - 作者：David Barr
 - 证书：Artistic

0x01 dnswalk功能
---------------

```shell
root@kali:~# dnswalk --help

用法: dnswalk [-选项[-更多选项]] [--] [程序参数1 ...]

接受以下单字符选项:
该选项有参数: -D
布尔型(没有参数): -r -f -i -a -d -m -F -l

选项可以合并在一起，--stop选项不做合并处理
选项及其参数之间不需要空

示例: dnswalk domain.com.
输入的域名必须以'.'结束
```

```shell
-r     递归向下查询指定域的子域
-a     打开重复A记录的警告
-d     打印调试和'状态'信息到stderr（仅在重定向stdout时使用）
-m     仅在上次运行后域已被修改时才执行检查
-F     执行"fascist"检查，在检查A记录时，不匹配每个IP地址的PTR名称与转发名称和报告
-i     禁止检查域名中的无效字符
-l     执行"lame delegation"检查。 对于每个NS记录，检查列出的主机是否确实是此域返回的权威答应。
```
0x02 dnswalk用法示例
-----------------

```shell
root@kali:~# dnswalk www.harvard.edu.
Checking www.harvard.edu.
BAD: SOA record not found for www.harvard.edu.
BAD: www.harvard.edu. has NO authoritative nameservers!
BAD: All zone transfer attempts of www.harvard.edu. failed!
0 failures, 0 warnings, 3 errors.
```
现在大多都没有域传送的漏洞了，这个工具现在比较鸡肋。

  [1]: http://sourceforge.net/projects/dnswalk/
  [2]: http://tools.kali.org/information-gathering/dnswalk