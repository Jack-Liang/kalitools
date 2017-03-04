#acccheck包描述

该工具被设计为一个密码字典攻击工具，目标是通过SMB协议的Windows身份验证。它实际上是围绕“smbclient”二进制文件的包装器脚本，因此依赖于它的执行。

**资料来源**： https : //labs.portcullis.co.uk/tools/acccheck/ 

[acccheck主页](http://labs.portcullis.co.uk/application/acccheck) | [Kali acccheck Repo](http://git.kali.org/gitweb/?p=packages/acccheck.git;a=summary)

- 作者：Faisal Dean
- 许可证：GPLv2

##acccheck包中包含的工具

###acccheck - SMB的密码字典攻击工具

```
root @ kali：〜＃acccheck 

acccheck v0.2.1 - Faiz 

说明：
尝试连接到IPC $和ADMIN $共享取决于选择哪些标志，
并尝试用户名和密码的组合，
希望通过字典密码猜测攻击识别给定帐户的密码。

用法= ./acccheck [可选] 

-t [单个主机IP地址] 
或 
-T [包含目标IP地址的文件] 

可选：
-p [单个密码] 
-P [包含密码的文件] 
-u [单个用户]
-U [包含用户名的文件] 
-v [详细模式] 

示例
使用[BLANK]密码尝试“Administrator”帐户。
acccheck -t 10.10.10.1。
尝试在“password.txt”中针对“Administrator”帐户的所有密码。
acccheck -t 10.10.10.1 -P password.txt 
对“users.txt”中的所有用户尝试“password.txt”中的所有密码。
acccehck -t 10.10.10.1 -U users.txt -P password.txt 
对单个用户尝试单个密码。
acccheck -t 10.10.10.1 -u administrator -p 密码
```

##acccheck用法示例

扫描smb-ips.txt（-T）中包含的IP地址，并使用详细输出（-v）：

```
root@kali:~# acccheck.pl -T smb-ips.txt -v
主机：192.168.1.201，用户名：Administrator，密码：BLANK
```

原文链接：http://tools.kali.org/information-gathering/acccheck
