---
title: iSMTP
categories: Information Gathering
tags: [recon,smtp,sniffing,spoofing,information gathering,kali linux,ismtp]
date: 2017-04-23 09:13:00
---
0x00 介绍
-------
测试SMTP用户枚举（RCPT TO和VRFY），内部欺骗和转发。

<!--more-->

[主页][1] | [仓库][2]

 - 作者：Alton Johnson
 - 证书：GPLv2

0x01 功能
ismtp - SMTP用户枚举和测试工具
-------
```plain
root@kali:~# ismtp

 ---------------------------------------------------------------------
  iSMTP v1.6 - SMTP Server Tester, Alton Johnson (alton.jx@gmail.com)
 ---------------------------------------------------------------------

 用法: ./iSMTP.py <选项>

 必需:

    -f <import file>    导入用于测试的SMTP服务器列表(不能同时使用'-h')
    -h <host>           目标IP和端口(格式 IP:port)(不能同时使用'-f')

 欺骗:

    -i <isa email>      互联网安全加速(Internet Security and Acceleration,ISA)电子邮件地址。
    -s <sndr email>     发件人电子邮件地址。
    -r <rcpt email>     收件人电子邮件地址。
       --sr <email>     指定发件人和收件人电子邮件地址。
    -S <sndr name>      发件人姓名。
    -R <rcpt name>      收件人姓名。
       --SR <name>      指定发件人和收件人姓名。
    -m                  启用S​​MTP欺骗测试。
    -a                  附带欺骗邮件的.txt附件。

 SMTP枚举:

    -e <file>           启用S​​MTP用户枚举测试并导入电子邮件列表。
    -l <1|2|3>          指定枚举类型(1 = VRFY, 2 = RCPT TO, 3 = all).(默认第3种)

 SMTP转发:

    -i <isa email>      互联网安全加速(Internet Security and Acceleration,ISA)电子邮件地址。
    -x                  启用S​​MTP外部转发测试。

 其他:

    -t <secs>           超时值(Default is 10.)
    -o                  创建“ismtp-results”目录并将输出写入到ismtp-results/smtp_<service>_<ip>(port).txt

注意：支持任何选项的组合（例如枚举，转发，两者组合，所有组合等）。
```
0x02 示例
-------
Test a list of IPs from a file (-f smtp-ips.txt) enumerating usernames from a dictionary file (-e /usr/share/wordlists/metasploit/unix_users.txt):
从一个IP列表文件（-f smtp-ips.txt）中枚举来自字典文件（-e /usr/share/wordlists/metasploit/unix_users.txt）的用户：
```plain
root@kali:~# ismtp -f smtp-ips.txt -e /usr/share/wordlists/metasploit/unix_users.txt

 ---------------------------------------------------------------------
  iSMTP v1.6 - SMTP Server Tester, Alton Johnson (alton.jx@gmail.com)
 ---------------------------------------------------------------------

 Testing SMTP server [user enumeration]: 192.168.1.25:25
 Emails provided for testing: 109

 Performing SMTP VRFY test...

 [-] 4Dgifts ------------- [ invalid ]
 [-] EZsetup ------------- [ invalid ]
 [+] ROOT ---------------- [ success ]
 [+] adm ----------------- [ success ]
```


  [1]: https://github.com/altjx/ipwn/
  [2]: http://git.kali.org/gitweb/?p=packages/ismtp.git;a=summary
