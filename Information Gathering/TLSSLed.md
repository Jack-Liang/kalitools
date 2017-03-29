# TLSSLed软件包描述

TLSSLed是一个Linux shell脚本，其目的是评估目标SSL/TLS（HTTPS）Web服务器实现的安全性。它基于sslscan和“openssl s_client”命令行工具，sslscan是一个使用openssl库全面的SSL/TLS扫描器。 目前的测试包括检查目标是否支持SSLv2协议、空密码、弱密码（长度40或56位）、强密码（如AES）的可用性、数字证书是否MD5签名，以及当前的SSL/TLS重协商功能。

资料来源：http://www.taddong.com/en/lab.html

[TLSSLed首页](http://www.taddong.com/en/lab.html) | [Kali TLSSLed资源](http://git.kali.org/gitweb/?p=packages/tlssled.git;a=summary)

- 作者：Raul Siles，Taddong SL
- 许可证：GPLv3

## TLSSLed包含的工具
### tlssled - 评估目标SSL/TLS（HTTPS）服务器的安全性
```
root@kali:~# tlssled
------------------------------------------------------
 TLSSLed - (1.3) based on sslscan and openssl
                 by Raul Siles (www.taddong.com)
------------------------------------------------------
    openssl version: OpenSSL 1.0.1e 11 Feb 2013
    sslscan version 1.8.2
------------------------------------------------------
    Date: 20140520-110731
------------------------------------------------------

[!] 用法: /usr/bin/tlssled <主机名或IP地址> <端口>
```
## TLSSLed使用示例

检查主机192.168.1.1和端口443上的SSL/TLS：
```
root@kali:~# tlssled 192.168.1.1 443
------------------------------------------------------
 TLSSLed - (1.3) based on sslscan and openssl
                 by Raul Siles (www.taddong.com)
------------------------------------------------------
    openssl version: OpenSSL 1.0.1e 11 Feb 2013
    sslscan version 1.8.2
------------------------------------------------------
    Date: 20140513-165131
------------------------------------------------------

[*] 分析192.168.1.1:443上的SSL/TLS...
    [.] 输出目录: TLSSLed_1.3_192.168.1.1_443_20140513-165131 ...

[*] 检查目标是否支持SSL/TLS...
    [.] 目标192.168.1.1:443支持SSL/TLS...

    [.] 使用的SSL/TLS协议版本:
        (空意味着正在使用默认的openssl协议版本)

[*] 在192.168.1.1:443上运行sslscan...

    [-] 测试SSLv2 ...

    [-] 测试空密码...
```

原文链接：[http://tools.kali.org/information-gathering/tlssled](http://tools.kali.org/information-gathering/tlssled)
