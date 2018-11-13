---
title: Cookie Cadger
categories: Information Gathering
tags: [cookie cadger,information gathering,spoofing,sniffing,kali linux]
date: 2016-10-19 15:26:49
---
0x00 Cookie Cadger介绍
-------------

Cookie Cadger有助于识别使用不安全HTTP GET请求应用程序中的泄漏的信息。

自2010年Firesheep发布以来，网络提供商已开始逐步升级。如今，大多数主要网站可以在都在使用SSL/TLS协议，防止Cookie数据通过有线以太网或不安全的Wi-Fi泄漏。但实际上是，Firesheep更多的只是一个玩具，而不是一个工具。 Cookie Cadger是第一个用于拦截和重放特定的不安全的HTTP GET请求到浏览器中的开源渗透测试工具。

Cookie Cadgers请求枚举功能

Cookie Cadger是一个图形实用程序，利用Wireshark套件和Java的强大功能提供一个完全跨平台，完全开源的实用程序，可以监视有线以太网，不安全的Wi-Fi或加载数据包捕获文件进行离线分析。

工具来源：https://www.cookiecadger.com/

[Cookie Cadger主页][1] | [Kali Cookie Cadger Repo仓库][2]

 - 作者：Matthew Sullivan
 - 证书：FreeBSD

0x01 Cookie Cadger功能
---------------

cdpsnarf - 有线和无线网络的Cookie工具

```shell
root@kali:~# cookie-cadger --help
Cookie Cadger, version 1.07
用法示例：
java -jar CookieCadger.jar
    --tshark=/usr/sbin/tshark
    --headless=on
    --interfacenum=2    (需要设置 --headless=on)
    --detection=on
    --demo=on
    --update=on
    --dbengine=mysql    (对于基于本地存储的文件，默认值为'sqlite')
    --dbhost=localhost  (需要设置 --dbengine=mysql)
    --dbuser=user       (需要设置 --dbengine=mysql)
    --dbpass=pass       (需要设置 --dbengine=mysql)
    --dbname=cadgerdata (需要设置 --dbengine=mysql)
    --dbrefreshrate=15  (以秒为单位，需要设置 --dbengine=mysql，需要设置 --headless=off)
```

0x02 Cookie Cadger用法示例
-----------------

```shell
root@kali:~# cookie-cadger
```
![cookie-cadger.png][3]

0x03 说明
-------

最新版本的Kali已经移除了Cookie Cadger，你可以使用以下命令获取并安装：
```shell
root@kali:~# wget https://www.cookiecadger.com/files/CookieCadger-1.08.jar
root@kali:~# chmod +x CookieCadger-1.08.jar
root@kali:~# mv CookieCadger-1.08.jar /usr/bin/
```
推荐Cookie Cadger官方说明文档：[An Auditing Tool for Wi-Fi or Wired Ethernet Connections][4]

  [1]: https://www.cookiecadger.com/
  [2]: http://git.kali.org/gitweb/?p=packages/cookie-cadger.git;a=summary
  [3]: https://www.hackfun.org/usr/uploads/2016/10/4222776969.png
  [4]: https://www.cookiecadger.com/wp-content/uploads/Cookie%20Cadger.pdf