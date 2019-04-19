---
title: APT2
categories: Information Gathering
tags: [kali linux,APT2,information gathering,Penetration]
date: 2019-04-19 17:47:00
---

APT2 Package Description
========================

自动渗透测试工具包。

此工具将执行NMap扫描，或从Nexpose，Nessus或NMap导入扫描结果。 处理结果将用于根据可配置的安全级别和枚举服务信息启动漏洞利用和枚举模块。

所有模块结果都存储在localhost中，并且是APT2知识库（KB）的一部分。 可以从应用程序中访问KB，并允许用户查看漏洞利用模块的收集结果。

工具来源: https://github.com/MooseDojo/apt2

[主页][1] | [仓库][2]

作者：Adam Compton 、 Austin Lane

证书：MIT

APT2 帮助
=========

```
root@kali:~# apt2 -h

用法： apt2 [-h] [-C <config.txt>] [-f [<input file> [<input file> ...]]]
            [--target] [--ip <local IP>] [-v] [-s SAFE_LEVEL]
            [-x EXCLUDE_TYPES] [-b] [--listmodules]

可选参数：

  -h, --help            显示此帮助消息并退出
  -v, --verbosity       增加输出冗长度
  -s SAFE_LEVEL, --safelevel SAFE_LEVEL
                        设置模块的最低安全级别。0表示不安全，5表示非常安全。
                        默认值为4
  -x EXCLUDE_TYPES, --exclude EXCLUDE_TYPES
                        指定要从运行得模块中排除的类型，用逗号分隔
  -b, --bypassmenu      绕过菜单并从命令行参数运行
  
  输入:
  -C <config.txt>       配置文件
  -f [<input file> [<input file> ...]]
                        由空格分隔的一个或多个输入文件
  --target              初始扫描目标
  
  高级选项:
  --ip <local IP>       默认值为 192.168.103.227
  
  其他:
  --listmodules         列出当前所有模块并退出

root@kali:~#
root@kali:~#
root@kali:~# apt2 --listmodules | grep '|' | sort | grep -v 'Module.*Type.*Description'
[*] | anonftp                   | action |      4 | Test for Anonymous FTP                                                                    |
[*] | anonldap                  | action |      5 | Test for Anonymous LDAP Searches                                                          |
[*] | apt2_ipwhois              | action |      5 | run ipwhois                                                                               |
[*] | apt2_shodan               | action |      5 | run shodan                                                                                |
[*] | apt2_whois                | action |      5 | run whois                                                                                 |
[*] | crackPasswordHashJohnTR   | action |      5 | Attempt to crack any password hashes                                                      |
[*] | dictload                  | input  |      None  | Load DICT Input File                                                                      |
[*] | gethostname               | action |      5 | Determine the hostname for each IP                                                        |
[*] | httpoptions               | action |      5 | Get HTTP Options                                                                          |
[*] | httpscreenshot            | action |      5 | Get Screen Shot of Web Pages                                                              |
[*] | httpserverversion         | action |      5 | Get HTTP Server Version                                                                   |
[*] | hydrasmbpassword          | action |      2 | Attempt to bruteforce SMB passwords                                                       |
[*] | impacketsecretsdump       | action |      5 | Test for NULL Session                                                                     |
[*] | msf_dumphashes            | action |      4 | Gather hashes from MSF Sessions                                                           |
[*] | msf_gathersessioninfo     | action |      4 | Get Info about any new sessions                                                           |
[*] | msf_javarmi               | action |      5 | Attempt to Exploit A Java RMI Service                                                     |
[*] | msf_jboss_maindeployer    | action |      3 | Attempt to gain shell via Jboss                                                           |
[*] | msf_jboss_vulnscan        | action |      4 | Attempt to determine if a jboss instance has default creds                                |
[*] | msf_ms08_067              | action |      4 | Attempt to exploit MS08-067                                                               |
[*] | msf_openx11               | action |      5 | Attempt Login To Open X11 Service                                                         |
[*] | msf_psexec_pth            | action |      4 | Attempt to authenticate via PSEXEC PTH                                                    |
[*] | msf_smbuserenum           | action |      5 | Get List of Users From SMB                                                                |
[*] | msf_snmpenumshares        | action |      5 | Enumerate SMB Shares via LanManager OID Values                                            |
[*] | msf_snmpenumusers         | action |      5 | Enumerate Local User Accounts Using LanManager/psProcessUsername OID Values               |
[*] | msf_snmplogin             | action |      5 | Attempt Login Using Common Community Strings                                              |
[*] | msf_tomcat_mgr_login      | action |      4 | Attempt to determine if a tomcat instance has default creds                               |
[*] | msf_tomcat_mgr_upload     | action |      3 | Attempt to gain shell via Tomcat                                                          |
[*] | msf_vncnoneauth           | action |      5 | Detect VNC Services with the None authentication type                                     |
[*] | nmaploadxml               | input  |      None  | Load NMap XML File                                                                        |
[*] | nmapms08067scan           | action |      4 | NMap MS08-067 Scan                                                                        |
[*] | nmapnfsshares             | action |      5 | NMap NFS Share Scan                                                                       |
[*] | nmapsmbshares             | action |      5 | NMap SMB Share Scan                                                                       |
[*] | nmapsmbsigning            | action |      5 | NMap SMB-Signing Scan                                                                     |
[*] | nmapsslscan               | action |      5 | NMap SSL Scan                                                                             |
[*] | nmapvncbrute              | action |      5 | NMap VNC Brute Scan                                                                       |
[*] | nullsessionrpcclient      | action |      5 | Test for NULL Session                                                                     |
[*] | nullsessionsmbclient      | action |      5 | Test for NULL Session                                                                     |
[*] | openx11                   | action |      5 | Attempt Login To Open X11 Servicei and Get Screenshot                                     |
[*] | reportgen                 | report |      None  | Generate HTML Report                                                                      |
[*] | responder                 | action |      3 | Run Responder and watch for hashes                                                        |
[*] | searchftp                 | action |      4 | Search files on FTP                                                                       |
[*] | searchnfsshare            | action |      4 | Search files on NFS Shares                                                                |
[*] | searchsmbshare            | action |      4 | Search files on SMB Shares                                                                |
[*] | snmpwalk                  | action |      5 | Run snmpwalk using found community string                                                 |
[*] | sslsslscan                | action |      5 | Determine SSL protocols and ciphers                                                       |
[*] | ssltestsslserver          | action |      5 | Determine SSL protocols and ciphers                                                       |
[*] | userenumrpcclient         | action |      5 | Get List of Users From SMB  
root@kali:~#
```

APT2 用法示例
============

```
root@kali:~# msfdb start
[+] Starting database
root@kali:~# 
root@kali:~# msfconsole -q -x 'load msgrpc User=msf Pass=msfpass ServerPort=55552'
/usr/share/metasploit-framework/lib/msf/core/opt.rb:55: 警告: constant OpenSSL::SSL::SSLContext::METHODS is deprecated
[*] MSGRPC Service:  127.0.0.1:55552 
[*] MSGRPC Username: msf
[*] MSGRPC Password: msfpass
[*] Successfully loaded plugin: msgrpc
msf >


root@kali:~# apt2 -s 0 -b --target 192.168.103.128 
[*] 
[*]       dM.    `MMMMMMMb. MMMMMMMMMM      
[*]      ,MMb     MM    `Mb /   MM   \      
[*]      d'YM.    MM     MM     MM   ____   
[*]     ,P `Mb    MM     MM     MM  6MMMMb  
[*]     d'  YM.   MM    .M9     MM MM'  `Mb 
[*]    ,P   `Mb   MMMMMMM9'     MM      ,MM 
[*]    d'    YM.  MM            MM     ,MM' 
[*]   ,MMMMMMMMb  MM            MM   ,M'    
[*]   d'      YM. MM            MM ,M'      
[*] _dM_     _dMM_MM_          _MM_MMMMMMMM 
[*] 
[*] 
[*] An Automated Penetration Testing Toolkit
[*] Written by: Adam Compton & Austin Lane
[*] Verion: 1.0.0
[!] Module 'apt2_shodan' disabled:
[!]      API key is missing
[!] Module 'searchnfsshare' disabled:
[!]      Module Manually Disabled !!!
[*] Input Modules Loaded:   2
[*] Action Modules Loaded:  43
[*] Report Modules Loaded:  1
[*] 
[*] The KnowledgeBase will be auto saved to : /root/.apt2/proofs/KB-egghavrdqa.save
[*] Local IP is set to : 192.168.103.227
[*]       If you would rather use a different IP, then specify it via the [--ip <ip>] argument.
[*] Scan file saved to [/root/.apt2/proofs/NMAP-nmapScan192.168.103.128-fvqoswtplf]
[*] Use the following controls while scans are running:
[*] Starting responder...
[*] - p - pause/resume event queueing
[!] VULN [NULLSession] Found on [192.168.103.128]
[*] Current # of Active Threads = [10]
[*]     ==> Responder, GetHostname, MSFJbossVulnscan, MSFTomcatMgrLogin, MSFJbossVulnscan, MSFTomcatMgrLogin, NmapMS08067Scan, NmapSMBSigning, NmapSMBShareScan, MSFSMBUserEnum
[*] Current # of Active Threads = [10]
[*]     ==> Responder, GetHostname, MSFJbossVulnscan, MSFTomcatMgrLogin, MSFJbossVulnscan, MSFTomcatMgrLogin, NmapMS08067Scan, NmapSMBSigning, NmapSMBShareScan, MSFSMBUserEnum
[*] Current # of Active Threads = [9]
[*]     ==> Responder, MSFJbossVulnscan, MSFTomcatMgrLogin, MSFJbossVulnscan, MSFTomcatMgrLogin, NmapMS08067Scan, NmapSMBSigning, NmapSMBShareScan, MSFSMBUserEnum
[*] Scan file saved to [/root/.apt2/proofs/NMAP-192.168.103.128_MS08067SCAN-ughssbeike]
[*] Scan file saved to [/root/.apt2/proofs/NMAP-192.168.103.128_SMBSINGINGSCAN-mcjojhzjny]
[*] Scan file saved to [/root/.apt2/proofs/NMAP-192.168.103.128_SMBSHARESCAN-idhndqdplo]
[*] Current # of Active Threads = [6]
[*]     ==> Responder, MSFJbossVulnscan, MSFTomcatMgrLogin, MSFJbossVulnscan, MSFTomcatMgrLogin, MSFSMBUserEnum
[*] Current # of Active Threads = [6]
[*]     ==> Responder, MSFJbossVulnscan, MSFTomcatMgrLogin, MSFJbossVulnscan, MSFTomcatMgrLogin, MSFSMBUserEnum
[*] Current # of Active Threads = [6]
[*]     ==> Responder, MSFJbossVulnscan, MSFTomcatMgrLogin, MSFJbossVulnscan, MSFTomcatMgrLogin, MSFSMBUserEnum
[*] Current # of Active Threads = [1]
[*]     ==> Responder
[*] Current # of Active Threads = [1]
[*]     ==> Responder
[*] Current # of Active Threads = [1]
[*]     ==> Responder
[*] Generating Reports
[*] Report file located at /root/.apt2/reports/reportGenHTML_shfrqjwgxs.html
[*] 
[*] Good Bye!
root@kali:~# 
root@kali:~# 
root@kali:~# tree  /root/.apt2/
/root/.apt2/
├── logs
│   └── processlog.txt
├── proofs
│   ├── httpOptions_192.168.103.128_80_vnkzicnlst
│   ├── HTTPServerVersion_192.168.103.128_443_tzeexsuztp
│   ├── HTTPServerVersion_192.168.103.128_80_awllaokxlc
│   ├── KB-egghavrdqa.save
│   ├── MSFJbossVulnscan_192.168.103.128_bcchobmmzp
│   ├── MSFJbossVulnscan_192.168.103.128_mbpdgqtezt
│   ├── MSFSMBUserEnum_192.168.103.128_krcyxrdotc
│   ├── MSFTomcatMgrLogin_192.168.103.128_pqvkxxjweb
│   ├── MSFTomcatMgrLogin_192.168.103.128_stccicqbwu
│   ├── NMAP-192.168.103.128_MS08067SCAN-ughssbeike.gnmap
│   ├── NMAP-192.168.103.128_MS08067SCAN-ughssbeike.nmap
│   ├── NMAP-192.168.103.128_MS08067SCAN-ughssbeike.xml
│   ├── NMAP-192.168.103.128_SMBSHARESCAN-idhndqdplo.gnmap
│   ├── NMAP-192.168.103.128_SMBSHARESCAN-idhndqdplo.nmap
│   ├── NMAP-192.168.103.128_SMBSHARESCAN-idhndqdplo.xml
│   ├── NMAP-192.168.103.128_SMBSINGINGSCAN-mcjojhzjny.gnmap
│   ├── NMAP-192.168.103.128_SMBSINGINGSCAN-mcjojhzjny.nmap
│   ├── NMAP-192.168.103.128_SMBSINGINGSCAN-mcjojhzjny.xml
│   ├── NMAP-nmapScan192.168.103.128-fvqoswtplf.gnmap
│   ├── NMAP-nmapScan192.168.103.128-fvqoswtplf.nmap
│   ├── NMAP-nmapScan192.168.103.128-fvqoswtplf.xml
│   ├── nmblookup_192.168.103.128_fkiytphaty
│   ├── nmblookup_192.168.103.128_jhklrjsumn
│   ├── nmblookup_192.168.103.128_pcbiyotbkm
│   ├── NULLSessionRpcClient_192.168.103.128_lfidievfys
│   ├── NULLSessionSmbClient_192.168.103.128_kgixcdjuse
│   ├── Responder_rlxujzjrqo
│   ├── Responder_tgtekbrxou
│   └── UserEnumRpcClient_192.168.103.128_nehnpiwedo
├── reports
│   └── reportGenHTML_shfrqjwgxs.html
└── tmp

4 directories, 31 files
root@kali:~# 
root@kali:~# 
root@kali:~# firefox /root/.apt2/reports/reportGenHTML_shfrqjwgxs.html
```


  [1]: https://github.com/MooseDojo/apt2
  [2]: http://git.kali.org/gitweb/?p=packages/apt2.git
