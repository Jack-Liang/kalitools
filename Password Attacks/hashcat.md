# Hashcat

## Hashcat软件描述
hashcat是世界上最快、最先进的密码恢复工具，支持五种独特的模式攻击超过200种哈希算法。hashcat目前支持Linux、Windows和OSX上的cpu、gpu和其他硬件加速器，并具有支持分布式密码破解的功能。

资料来源：https://github.com/hashcat/hashcat/

[hashcat主页](https://hashcat.net/hashcat/) | [Kali hashcat软件源](http://git.kali.org/gitweb/?p=packages/hashcat.git)

- 作者：atom
- 许可：Expat

### hashcat包含的工具
hashcat - 世界上最快、最先进的密码恢复工具
```
root@kali:~# hashcat --help
hashcat - advanced password recovery

Usage: hashcat [options]... hash|hashfile|hccapxfile [dictionary|mask|directory]...

- [ Options ] -

 Options Short / Long          | Type | Description                                          | Example
===============================+======+======================================================+=======================
 -m, --hash-type               | Num  | 哈希类型, 见下文　                                     | -m 1000
 -a, --attack-mode             | Num  | 攻击模式, 见下文　                                     | -a 3
 -V, --version                 |      | 打印版本信息     　　                                  |
 -h, --help                    |      | 打印帮助            　                                |
     --quiet                   |      | 静默输出                                              |
     --hex-charset             |      | 假定输入的字符集为十六进制表示                           |
     --hex-salt                |      | 假定盐值为十六进制表示                                  |
     --hex-wordlist            |      | 假定字典为十六进制表示                                  |
     --force                   |      | 忽略警告                                              |
     --status                  |      | 自动更新状态显示       　　                             |
     --status-timer            | Num  | 设置状态显示更新的间隔秒数                               | --status-timer=1
     --machine-readable        |      | 用机器易识别的格式显示状态信息 　                         |
     --keep-guessing           |      | 破解后仍继续猜测               　                       |
     --loopback                |      | 在induct目录增加新的明文                                |
     --weak-hash-threshold     | Num  | 指定停止检查弱哈希的门限值        　                     | --weak=0
     --markov-hcstat           | File | 指定要使用的hcstat文件            　                    | --markov-hc=my.hcstat
     --markov-disable          |      | 禁用markov-chains, 模拟典型的暴力破解　                  |
     --markov-classic          |      | 启用典型的markov-chains, 不使用每位置模式                |
 -t, --markov-threshold        | Num  | 指定停止接受新的markov-chains的门限值     　             | -t 50
     --runtime                 | Num  | 指定运行多少秒后退出会话                    　           | --runtime=10
     --session                 | Str  | 定义会话名                                  　         | --session=mysession
     --restore                 |      | 恢复会话                                     　        |
     --restore-disable         |      | 不写恢复文件                                           |
     --restore-file-path       | File | 指定恢复文件路径                                　      | --restore-file-path=my.restore
 -o, --outfile                 | File | 指定输出文件                                           | -o outfile.txt
     --outfile-format          | Num  | 指定输出文件格式                                  　    | --outfile-format=7
     --outfile-autohex-disable |      | 输出中禁用$HEX[]格式                               　   |
     --outfile-check-timer     | Num  | 设置检查输出文件的时间间隔                               | --outfile-check=30
 -p, --separator               | Char | 设置hashlists和输出文件的分隔符                       　 | -p :
     --stdout                  |      | 不破解哈希, 仅打印候选项                  　             |
     --show                    |      | 比较hashlist和potfile(已破解的哈希文件); 显示已破解的哈希　|
     --left                    |      | 比较hashlist和potfile; 显示未破解的哈希           　     |
     --username                |      | 启用忽略hashfile中的用户名                         　   |
     --remove                  |      | 启用删除已破解的哈希                                    |
     --remove-timer            | Num  | 设置更新输入哈希文件的时间间隔                        　  | --remove-timer=30
     --potfile-disable         |      | 不写potfile                                           |
     --potfile-path            | Dir  | 指定potfile的路径                          　          | --potfile-path=my.pot
     --encoding-from           | Code | 指定内部字典的编码                                      | --encoding-from=iso-8859-15
     --encoding-to             | Code | 指定内部字典的编码                            　        | --encoding-to=utf-32le
     --debug-mode              | Num  | 指定调试模式(通过使用规则)                       　      | --debug-mode=4
     --debug-file              | File | 指定调试规则输出文件                                    | --debug-file=good.log
     --induction-dir           | Dir  | 指定用来本地查找的induction目录                 　      | --induction=inducts
     --outfile-check-dir       | Dir  | 指定用来检查明文输出文件的目录                           | --outfile-check-dir=x
     --logfile-disable         |      | 禁用日志文件                                           |
     --hccapx-message-pair     | Num  | 仅从hccapx加载匹配的消息对                              | --hccapx-message-pair=2
     --nonce-error-corrections | Num  | The BF size range to replace AP's nonce last bytes   | --nonce-error-corrections=16
     --truecrypt-keyfiles      | File | 指定Keyfiles, 用逗号分隔                               | --truecrypt-key=x.png
     --veracrypt-keyfiles      | File | 指定Keyfiles, 用逗号分隔                               | --veracrypt-key=x.txt
     --veracrypt-pim           | Num  | VeraCrypt personal iterations multiplier             | --veracrypt-pim=1000
 -b, --benchmark               |      | 运行基准测试                                 　        |
     --speed-only              |      | 返回预计的破解速度, 然后退出                     　      |
     --progress-only           |      | 返回预计的处理步骤内存占用和时间                    　    |
 -c, --segment-size            | Num  | 设置字典文件缓存大小MB                                  | -c 32
     --bitmap-min              | Num  | 设置bitmaps的最小位数                                  | --bitmap-min=24
     --bitmap-max              | Num  | 设置bitmaps的最大位数                                  | --bitmap-max=24
     --cpu-affinity            | Str  | 指定CPU, 用逗号分隔                                    | --cpu-affinity=1,2,3
 -I, --opencl-info             |      | 显示检测到的OpenCL平台/设备信息                      　  | -I
     --opencl-platforms        | Str  | 指定OpenCL平台, 用逗号分隔                              | --opencl-platforms=2
 -d, --opencl-devices          | Str  | 指定OpenCL设备, 用逗号分隔                              | -d 1
 -D, --opencl-device-types     | Str  | 指定OpenCL设备类型, 用逗号分隔          　               | -D 1
     --opencl-vector-width     | Num  | 手动覆盖OpenCL向量宽度                   　             | --opencl-vector=4
 -w, --workload-profile        | Num  | 指定工作负载配置文件, 见下面                             | -w 3
 -n, --kernel-accel            | Num  | 手动调优工作负载, 设置外部循环大小                        | -n 64
 -u, --kernel-loops            | Num  | 手动调优工作负载, 设置内部循环小小                        | -u 256
     --nvidia-spin-damp        | Num  | Workaround NVIDIAs CPU burning loop bug, in percent  | --nvidia-spin-damp=50
     --gpu-temp-disable        |      | 禁用温度和风扇速度监测报警                               |
     --gpu-temp-abort          | Num  | 当GPU温度达到指定摄氏度时退出                            | --gpu-temp-abort=100
     --gpu-temp-retain         | Num  | 尝试保持GPU温度在指定的摄氏度                            | --gpu-temp-retain=95
     --powertune-enable        |      | 启用电力调优. 完成后恢复设置                             |
     --scrypt-tmto             | Num  | Manually override TMTO value for scrypt to X         | --scrypt-tmto=3
 -s, --skip                    | Num  | 略过开始处的若干单词                                    | -s 1000000
 -l, --limit                   | Num  | 从略过处开始限制指定的单词数                             | -l 1000000
     --keyspace                |      | Show keyspace base:mod values and quit               |
 -j, --rule-left               | Rule | 对字典文件的每个单词从左侧应用单条规则             　      | -j 'c'
 -k, --rule-right              | Rule | 对字典文件的每个单词从右侧应用单条规则               　    | -k '^-'
 -r, --rules-file              | File | 对字典文件的每个单词应用多条规则                      　  | -r rules/best64.rule
 -g, --generate-rules          | Num  | 生成随机规则                            　             | -g 10000
     --generate-rules-func-min | Num  | Force min X functions per rule                       |
     --generate-rules-func-max | Num  | Force max X functions per rule                       |
     --generate-rules-seed     | Num  | 设置随机数种子                                         |
 -1, --custom-charset1         | CS   | 用户自定义字符集 ?1                       　　　        | -1 ?l?d?u
 -2, --custom-charset2         | CS   | 用户自定义字符集 ?2                            　　     | -2 ?l?d?s
 -3, --custom-charset3         | CS   | 用户自定义字符集 ?3                               　    |
 -4, --custom-charset4         | CS   | 用户自定义字符集 ?4                                 　　|
 -i, --increment               |      | 启用增量掩码模式                               　      |
     --increment-min           | Num  | 从指定处开始增量掩码                                    | --increment-min=4
     --increment-max           | Num  | 在指定处停止增量掩码                                    | --increment-max=8

- [ Hash modes ] -

      # | Name                                             | Category
  ======+==================================================+======================================
    900 | MD4                                              | Raw Hash
      0 | MD5                                              | Raw Hash
   5100 | Half MD5                                         | Raw Hash
    100 | SHA1                                             | Raw Hash
   1300 | SHA-224                                          | Raw Hash
   1400 | SHA-256                                          | Raw Hash
  10800 | SHA-384                                          | Raw Hash
   1700 | SHA-512                                          | Raw Hash
   5000 | SHA-3 (Keccak)                                   | Raw Hash
    600 | BLAKE2b-512                                      | Raw Hash
  10100 | SipHash                                          | Raw Hash
   6000 | RIPEMD-160                                       | Raw Hash
   6100 | Whirlpool                                        | Raw Hash
   6900 | GOST R 34.11-94                                  | Raw Hash
  11700 | GOST R 34.11-2012 (Streebog) 256-bit             | Raw Hash
  11800 | GOST R 34.11-2012 (Streebog) 512-bit             | Raw Hash
     10 | md5($pass.$salt)                                 | Raw Hash, Salted and/or Iterated
     20 | md5($salt.$pass)                                 | Raw Hash, Salted and/or Iterated
     30 | md5(utf16le($pass).$salt)                        | Raw Hash, Salted and/or Iterated
     40 | md5($salt.utf16le($pass))                        | Raw Hash, Salted and/or Iterated
   3800 | md5($salt.$pass.$salt)                           | Raw Hash, Salted and/or Iterated
   3710 | md5($salt.md5($pass))                            | Raw Hash, Salted and/or Iterated
   4010 | md5($salt.md5($salt.$pass))                      | Raw Hash, Salted and/or Iterated
   4110 | md5($salt.md5($pass.$salt))                      | Raw Hash, Salted and/or Iterated
   2600 | md5(md5($pass))                                  | Raw Hash, Salted and/or Iterated
   3910 | md5(md5($pass).md5($salt))                       | Raw Hash, Salted and/or Iterated
   4300 | md5(strtoupper(md5($pass)))                      | Raw Hash, Salted and/or Iterated
   4400 | md5(sha1($pass))                                 | Raw Hash, Salted and/or Iterated
    110 | sha1($pass.$salt)                                | Raw Hash, Salted and/or Iterated
    120 | sha1($salt.$pass)                                | Raw Hash, Salted and/or Iterated
    130 | sha1(utf16le($pass).$salt)                       | Raw Hash, Salted and/or Iterated
    140 | sha1($salt.utf16le($pass))                       | Raw Hash, Salted and/or Iterated
   4500 | sha1(sha1($pass))                                | Raw Hash, Salted and/or Iterated
   4520 | sha1($salt.sha1($pass))                          | Raw Hash, Salted and/or Iterated
   4700 | sha1(md5($pass))                                 | Raw Hash, Salted and/or Iterated
   4900 | sha1($salt.$pass.$salt)                          | Raw Hash, Salted and/or Iterated
  14400 | sha1(CX)                                         | Raw Hash, Salted and/or Iterated
   1410 | sha256($pass.$salt)                              | Raw Hash, Salted and/or Iterated
   1420 | sha256($salt.$pass)                              | Raw Hash, Salted and/or Iterated
   1430 | sha256(utf16le($pass).$salt)                     | Raw Hash, Salted and/or Iterated
   1440 | sha256($salt.utf16le($pass))                     | Raw Hash, Salted and/or Iterated
   1710 | sha512($pass.$salt)                              | Raw Hash, Salted and/or Iterated
   1720 | sha512($salt.$pass)                              | Raw Hash, Salted and/or Iterated
   1730 | sha512(utf16le($pass).$salt)                     | Raw Hash, Salted and/or Iterated
   1740 | sha512($salt.utf16le($pass))                     | Raw Hash, Salted and/or Iterated
     50 | HMAC-MD5 (key = $pass)                           | Raw Hash, Authenticated
     60 | HMAC-MD5 (key = $salt)                           | Raw Hash, Authenticated
    150 | HMAC-SHA1 (key = $pass)                          | Raw Hash, Authenticated
    160 | HMAC-SHA1 (key = $salt)                          | Raw Hash, Authenticated
   1450 | HMAC-SHA256 (key = $pass)                        | Raw Hash, Authenticated
   1460 | HMAC-SHA256 (key = $salt)                        | Raw Hash, Authenticated
   1750 | HMAC-SHA512 (key = $pass)                        | Raw Hash, Authenticated
   1760 | HMAC-SHA512 (key = $salt)                        | Raw Hash, Authenticated
  14000 | DES (PT = $salt, key = $pass)                    | Raw Cipher, Known-Plaintext attack
  14100 | 3DES (PT = $salt, key = $pass)                   | Raw Cipher, Known-Plaintext attack
  14900 | Skip32 (PT = $salt, key = $pass)                 | Raw Cipher, Known-Plaintext attack
  15400 | ChaCha20                                         | Raw Cipher, Known-Plaintext attack
    400 | phpass                                           | Generic KDF
   8900 | scrypt                                           | Generic KDF
  11900 | PBKDF2-HMAC-MD5                                  | Generic KDF
  12000 | PBKDF2-HMAC-SHA1                                 | Generic KDF
  10900 | PBKDF2-HMAC-SHA256                               | Generic KDF
  12100 | PBKDF2-HMAC-SHA512                               | Generic KDF
     23 | Skype                                            | Network Protocols
   2500 | WPA/WPA2                                         | Network Protocols
   4800 | iSCSI CHAP authentication, MD5(CHAP)             | Network Protocols
   5300 | IKE-PSK MD5                                      | Network Protocols
   5400 | IKE-PSK SHA1                                     | Network Protocols
   5500 | NetNTLMv1                                        | Network Protocols
   5500 | NetNTLMv1+ESS                                    | Network Protocols
   5600 | NetNTLMv2                                        | Network Protocols
   7300 | IPMI2 RAKP HMAC-SHA1                             | Network Protocols
   7500 | Kerberos 5 AS-REQ Pre-Auth etype 23              | Network Protocols
   8300 | DNSSEC (NSEC3)                                   | Network Protocols
  10200 | CRAM-MD5                                         | Network Protocols
  11100 | PostgreSQL CRAM (MD5)                            | Network Protocols
  11200 | MySQL CRAM (SHA1)                                | Network Protocols
  11400 | SIP digest authentication (MD5)                  | Network Protocols
  13100 | Kerberos 5 TGS-REP etype 23                      | Network Protocols
    121 | SMF (Simple Machines Forum) > v1.1               | Forums, CMS, E-Commerce, Frameworks
    400 | phpBB3 (MD5)                                     | Forums, CMS, E-Commerce, Frameworks
   2611 | vBulletin < v3.8.5                               | Forums, CMS, E-Commerce, Frameworks
   2711 | vBulletin >= v3.8.5                              | Forums, CMS, E-Commerce, Frameworks
   2811 | MyBB 1.2+                                        | Forums, CMS, E-Commerce, Frameworks
   2811 | IPB2+ (Invision Power Board)                     | Forums, CMS, E-Commerce, Frameworks
   8400 | WBB3 (Woltlab Burning Board)                     | Forums, CMS, E-Commerce, Frameworks
     11 | Joomla < 2.5.18                                  | Forums, CMS, E-Commerce, Frameworks
    400 | Joomla >= 2.5.18 (MD5)                           | Forums, CMS, E-Commerce, Frameworks
    400 | WordPress (MD5)                                  | Forums, CMS, E-Commerce, Frameworks
   2612 | PHPS                                             | Forums, CMS, E-Commerce, Frameworks
   7900 | Drupal7                                          | Forums, CMS, E-Commerce, Frameworks
     21 | osCommerce                                       | Forums, CMS, E-Commerce, Frameworks
     21 | xt:Commerce                                      | Forums, CMS, E-Commerce, Frameworks
  11000 | PrestaShop                                       | Forums, CMS, E-Commerce, Frameworks
    124 | Django (SHA-1)                                   | Forums, CMS, E-Commerce, Frameworks
  10000 | Django (PBKDF2-SHA256)                           | Forums, CMS, E-Commerce, Frameworks
   3711 | MediaWiki B type                                 | Forums, CMS, E-Commerce, Frameworks
  13900 | OpenCart                                         | Forums, CMS, E-Commerce, Frameworks
   4521 | Redmine                                          | Forums, CMS, E-Commerce, Frameworks
   4522 | PunBB                                            | Forums, CMS, E-Commerce, Frameworks
  12001 | Atlassian (PBKDF2-HMAC-SHA1)                     | Forums, CMS, E-Commerce, Frameworks
     12 | PostgreSQL                                       | Database Server
    131 | MSSQL (2000)                                     | Database Server
    132 | MSSQL (2005)                                     | Database Server
   1731 | MSSQL (2012, 2014)                               | Database Server
    200 | MySQL323                                         | Database Server
    300 | MySQL4.1/MySQL5                                  | Database Server
   3100 | Oracle H: Type (Oracle 7+)                       | Database Server
    112 | Oracle S: Type (Oracle 11+)                      | Database Server
  12300 | Oracle T: Type (Oracle 12+)                      | Database Server
   8000 | Sybase ASE                                       | Database Server
    141 | Episerver 6.x < .NET 4                           | HTTP, SMTP, LDAP Server
   1441 | Episerver 6.x >= .NET 4                          | HTTP, SMTP, LDAP Server
   1600 | Apache $apr1$ MD5, md5apr1, MD5 (APR)            | HTTP, SMTP, LDAP Server
  12600 | ColdFusion 10+                                   | HTTP, SMTP, LDAP Server
   1421 | hMailServer                                      | HTTP, SMTP, LDAP Server
    101 | nsldap, SHA-1(Base64), Netscape LDAP SHA         | HTTP, SMTP, LDAP Server
    111 | nsldaps, SSHA-1(Base64), Netscape LDAP SSHA      | HTTP, SMTP, LDAP Server
   1411 | SSHA-256(Base64), LDAP {SSHA256}                 | HTTP, SMTP, LDAP Server
   1711 | SSHA-512(Base64), LDAP {SSHA512}                 | HTTP, SMTP, LDAP Server
  15000 | FileZilla Server >= 0.9.55                       | FTP Server
  11500 | CRC32                                            | Checksums
   3000 | LM                                               | Operating Systems
   1000 | NTLM                                             | Operating Systems
   1100 | Domain Cached Credentials (DCC), MS Cache        | Operating Systems
   2100 | Domain Cached Credentials 2 (DCC2), MS Cache 2   | Operating Systems
  15300 | DPAPI masterkey file v1 and v2                   | Operating Systems
  12800 | MS-AzureSync  PBKDF2-HMAC-SHA256                 | Operating Systems
   1500 | descrypt, DES (Unix), Traditional DES            | Operating Systems
  12400 | BSDi Crypt, Extended DES                         | Operating Systems
    500 | md5crypt, MD5 (Unix), Cisco-IOS $1$ (MD5)        | Operating Systems
   3200 | bcrypt $2*$, Blowfish (Unix)                     | Operating Systems
   7400 | sha256crypt $5$, SHA256 (Unix)                   | Operating Systems
   1800 | sha512crypt $6$, SHA512 (Unix)                   | Operating Systems
    122 | OSX v10.4, OSX v10.5, OSX v10.6                  | Operating Systems
   1722 | OSX v10.7                                        | Operating Systems
   7100 | OSX v10.8+ (PBKDF2-SHA512)                       | Operating Systems
   6300 | AIX {smd5}                                       | Operating Systems
   6700 | AIX {ssha1}                                      | Operating Systems
   6400 | AIX {ssha256}                                    | Operating Systems
   6500 | AIX {ssha512}                                    | Operating Systems
   2400 | Cisco-PIX MD5                                    | Operating Systems
   2410 | Cisco-ASA MD5                                    | Operating Systems
    500 | Cisco-IOS $1$ (MD5)                              | Operating Systems
   5700 | Cisco-IOS type 4 (SHA256)                        | Operating Systems
   9200 | Cisco-IOS $8$ (PBKDF2-SHA256)                    | Operating Systems
   9300 | Cisco-IOS $9$ (scrypt)                           | Operating Systems
     22 | Juniper NetScreen/SSG (ScreenOS)                 | Operating Systems
    501 | Juniper IVE                                      | Operating Systems
  15100 | Juniper/NetBSD sha1crypt                         | Operating Systems
   7000 | FortiGate (FortiOS)                              | Operating Systems
   5800 | Samsung Android Password/PIN                     | Operating Systems
  13800 | Windows Phone 8+ PIN/password                    | Operating Systems
   8100 | Citrix NetScaler                                 | Operating Systems
   8500 | RACF                                             | Operating Systems
   7200 | GRUB 2                                           | Operating Systems
   9900 | Radmin2                                          | Operating Systems
    125 | ArubaOS                                          | Operating Systems
   7700 | SAP CODVN B (BCODE)                              | Enterprise Application Software (EAS)
   7800 | SAP CODVN F/G (PASSCODE)                         | Enterprise Application Software (EAS)
  10300 | SAP CODVN H (PWDSALTEDHASH) iSSHA-1              | Enterprise Application Software (EAS)
   8600 | Lotus Notes/Domino 5                             | Enterprise Application Software (EAS)
   8700 | Lotus Notes/Domino 6                             | Enterprise Application Software (EAS)
   9100 | Lotus Notes/Domino 8                             | Enterprise Application Software (EAS)
    133 | PeopleSoft                                       | Enterprise Application Software (EAS)
  13500 | PeopleSoft PS_TOKEN                              | Enterprise Application Software (EAS)
  11600 | 7-Zip                                            | Archives
  12500 | RAR3-hp                                          | Archives
  13000 | RAR5                                             | Archives
  13200 | AxCrypt                                          | Archives
  13300 | AxCrypt in-memory SHA1                           | Archives
  13600 | WinZip                                           | Archives
  14700 | iTunes backup < 10.0                             | Backup
  14800 | iTunes backup >= 10.0                            | Backup
   62XY | TrueCrypt                                        | Full-Disk Encryption (FDE)
     X  | 1 = PBKDF2-HMAC-RIPEMD160                        | Full-Disk Encryption (FDE)
     X  | 2 = PBKDF2-HMAC-SHA512                           | Full-Disk Encryption (FDE)
     X  | 3 = PBKDF2-HMAC-Whirlpool                        | Full-Disk Encryption (FDE)
     X  | 4 = PBKDF2-HMAC-RIPEMD160 + boot-mode            | Full-Disk Encryption (FDE)
      Y | 1 = XTS  512 bit pure AES                        | Full-Disk Encryption (FDE)
      Y | 1 = XTS  512 bit pure Serpent                    | Full-Disk Encryption (FDE)
      Y | 1 = XTS  512 bit pure Twofish                    | Full-Disk Encryption (FDE)
      Y | 2 = XTS 1024 bit pure AES                        | Full-Disk Encryption (FDE)
      Y | 2 = XTS 1024 bit pure Serpent                    | Full-Disk Encryption (FDE)
      Y | 2 = XTS 1024 bit pure Twofish                    | Full-Disk Encryption (FDE)
      Y | 2 = XTS 1024 bit cascaded AES-Twofish            | Full-Disk Encryption (FDE)
      Y | 2 = XTS 1024 bit cascaded Serpent-AES            | Full-Disk Encryption (FDE)
      Y | 2 = XTS 1024 bit cascaded Twofish-Serpent        | Full-Disk Encryption (FDE)
      Y | 3 = XTS 1536 bit all                             | Full-Disk Encryption (FDE)
   8800 | Android FDE <= 4.3                               | Full-Disk Encryption (FDE)
  12900 | Android FDE (Samsung DEK)                        | Full-Disk Encryption (FDE)
  12200 | eCryptfs                                         | Full-Disk Encryption (FDE)
  137XY | VeraCrypt                                        | Full-Disk Encryption (FDE)
     X  | 1 = PBKDF2-HMAC-RIPEMD160                        | Full-Disk Encryption (FDE)
     X  | 2 = PBKDF2-HMAC-SHA512                           | Full-Disk Encryption (FDE)
     X  | 3 = PBKDF2-HMAC-Whirlpool                        | Full-Disk Encryption (FDE)
     X  | 4 = PBKDF2-HMAC-RIPEMD160 + boot-mode            | Full-Disk Encryption (FDE)
     X  | 5 = PBKDF2-HMAC-SHA256                           | Full-Disk Encryption (FDE)
     X  | 6 = PBKDF2-HMAC-SHA256 + boot-mode               | Full-Disk Encryption (FDE)
      Y | 1 = XTS  512 bit pure AES                        | Full-Disk Encryption (FDE)
      Y | 1 = XTS  512 bit pure Serpent                    | Full-Disk Encryption (FDE)
      Y | 1 = XTS  512 bit pure Twofish                    | Full-Disk Encryption (FDE)
      Y | 2 = XTS 1024 bit pure AES                        | Full-Disk Encryption (FDE)
      Y | 2 = XTS 1024 bit pure Serpent                    | Full-Disk Encryption (FDE)
      Y | 2 = XTS 1024 bit pure Twofish                    | Full-Disk Encryption (FDE)
      Y | 2 = XTS 1024 bit cascaded AES-Twofish            | Full-Disk Encryption (FDE)
      Y | 2 = XTS 1024 bit cascaded Serpent-AES            | Full-Disk Encryption (FDE)
      Y | 2 = XTS 1024 bit cascaded Twofish-Serpent        | Full-Disk Encryption (FDE)
      Y | 3 = XTS 1536 bit all                             | Full-Disk Encryption (FDE)
  14600 | LUKS                                             | Full-Disk Encryption (FDE)
   9700 | MS Office <= 2003 $0/$1, MD5 + RC4               | Documents
   9710 | MS Office <= 2003 $0/$1, MD5 + RC4, collider #1  | Documents
   9720 | MS Office <= 2003 $0/$1, MD5 + RC4, collider #2  | Documents
   9800 | MS Office <= 2003 $3/$4, SHA1 + RC4              | Documents
   9810 | MS Office <= 2003 $3, SHA1 + RC4, collider #1    | Documents
   9820 | MS Office <= 2003 $3, SHA1 + RC4, collider #2    | Documents
   9400 | MS Office 2007                                   | Documents
   9500 | MS Office 2010                                   | Documents
   9600 | MS Office 2013                                   | Documents
  10400 | PDF 1.1 - 1.3 (Acrobat 2 - 4)                    | Documents
  10410 | PDF 1.1 - 1.3 (Acrobat 2 - 4), collider #1       | Documents
  10420 | PDF 1.1 - 1.3 (Acrobat 2 - 4), collider #2       | Documents
  10500 | PDF 1.4 - 1.6 (Acrobat 5 - 8)                    | Documents
  10600 | PDF 1.7 Level 3 (Acrobat 9)                      | Documents
  10700 | PDF 1.7 Level 8 (Acrobat 10 - 11)                | Documents
   9000 | Password Safe v2                                 | Password Managers
   5200 | Password Safe v3                                 | Password Managers
   6800 | LastPass + LastPass sniffed                      | Password Managers
   6600 | 1Password, agilekeychain                         | Password Managers
   8200 | 1Password, cloudkeychain                         | Password Managers
  11300 | Bitcoin/Litecoin wallet.dat                      | Password Managers
  12700 | Blockchain, My Wallet                            | Password Managers
  15200 | Blockchain, My Wallet, V2                        | Password Managers
  13400 | KeePass 1 (AES/Twofish) and KeePass 2 (AES)      | Password Managers
  15500 | JKS Java Key Store Private Keys (SHA1)           | Password Managers
  15600 | Ethereum Wallet, PBKDF2-HMAC-SHA256              | Password Managers
  15700 | Ethereum Wallet, SCRYPT                          | Password Managers
  99999 | Plaintext                                        | Plaintext

- [ Outfile Formats ] -

  # | Format
 ===+========
  1 | hash[:salt]
  2 | plain
  3 | hash[:salt]:plain
  4 | hex_plain
  5 | hash[:salt]:hex_plain
  6 | plain:hex_plain
  7 | hash[:salt]:plain:hex_plain
  8 | crackpos
  9 | hash[:salt]:crack_pos
 10 | plain:crack_pos
 11 | hash[:salt]:plain:crack_pos
 12 | hex_plain:crack_pos
 13 | hash[:salt]:hex_plain:crack_pos
 14 | plain:hex_plain:crack_pos
 15 | hash[:salt]:plain:hex_plain:crack_pos

- [ Rule Debugging Modes ] -

  # | Format
 ===+========
  1 | Finding-Rule
  2 | Original-Word
  3 | Original-Word:Finding-Rule
  4 | Original-Word:Finding-Rule:Processed-Word

- [ Attack Modes ] -

  # | Mode
 ===+======
  0 | Straight
  1 | Combination
  3 | Brute-force
  6 | Hybrid Wordlist + Mask
  7 | Hybrid Mask + Wordlist

- [ Built-in Charsets ] -

  ? | Charset
 ===+=========
  l | abcdefghijklmnopqrstuvwxyz
  u | ABCDEFGHIJKLMNOPQRSTUVWXYZ
  d | 0123456789
  h | 0123456789abcdef
  H | 0123456789ABCDEF
  s |  !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
  a | ?l?u?d?s
  b | 0x00 - 0xff

- [ OpenCL Device Types ] -

  # | Device Type
 ===+=============
  1 | CPU
  2 | GPU
  3 | FPGA, DSP, Co-Processor

- [ Workload Profiles ] -

  # | Performance | Runtime | Power Consumption | Desktop Impact
 ===+=============+=========+===================+=================
  1 | Low         |   2 ms  | Low               | Minimal
  2 | Default     |  12 ms  | Economic          | Noticeable
  3 | High        |  96 ms  | High              | Unresponsive
  4 | Nightmare   | 480 ms  | Insane            | Headless

- [ Basic Examples ] -

  Attack-          | Hash- |
  Mode             | Type  | Example command
 ==================+=======+==================================================================
  Wordlist         | $P$   | hashcat -a 0 -m 400 example400.hash example.dict
  Wordlist + Rules | MD5   | hashcat -a 0 -m 0 example0.hash example.dict -r rules/best64.rule
  Brute-Force      | MD5   | hashcat -a 3 -m 0 example0.hash ?a?a?a?a?a?a
  Combinator       | MD5   | hashcat -a 1 -m 0 example0.hash example.dict example.dict

If you still have no idea what just happened, try the following pages:

* https://hashcat.net/wiki/#howtos_videos_papers_articles_etc_in_the_wild
* https://hashcat.net/faq/
```
### hashcat用法示例
对支持的哈希类型进行基准测试以确定破解速度。
```
root@kali:~# hashcat -b
hashcat (pull/1273/head) starting in benchmark mode...

OpenCL Platform #1: Mesa, skipped or no OpenCL compatible devices found.

OpenCL Platform #2: Intel(R) Corporation
========================================
* Device #1: Intel(R) Core(TM) i7-4500U CPU @ 1.80GHz, 3992/15970 MB allocatable, 4MCU

Hashtype: MD4

Speed.Dev.#1.....:   293.0 MH/s (14.21ms)

Hashtype: MD5

Speed.Dev.#1.....:   162.7 MH/s (25.73ms)
...
```
使用md5crypt模式(*-m 500*)，用提供的字典(*/usr/share/wordlists/sqlmap.txt*)破解示例哈希(*/usr/share/doc/hashcat-data/examples/example500.hash*)。
```
root@kali:~# hashcat -m 500 /usr/share/doc/hashcat-data/examples/example500.hash /usr/share/wordlists/sqlmap.txt
hashcat (pull/1273/head) starting...

OpenCL Platform #1: Mesa, skipped or no OpenCL compatible devices found.

OpenCL Platform #2: Intel(R) Corporation
========================================
* Device #1: Intel(R) Core(TM) i7-4500U CPU @ 1.80GHz, 3992/15970 MB allocatable, 4MCU

Hashes: 1 digests; 1 unique digests, 1 unique salts
Bitmaps: 16 bits, 65536 entries, 0x0000ffff mask, 262144 bytes, 5/13 rotates
Rules: 1

Applicable optimizers:
* Zero-Byte
* Single-Hash
* Single-Salt

Watchdog: Hardware monitoring interface not found on your system.
Watchdog: Temperature abort trigger disabled.
Watchdog: Temperature retain trigger disabled.

* Device #1: build_opts '-I /usr/share/hashcat/OpenCL -D VENDOR_ID=8 -D CUDA_ARCH=0 -D VECT_SIZE=8 -D DEVICE_TYPE=2 -D DGST_R0=0 -D DGST_R1=1 -D DGST_R2=2 -D DGST_R3=3 -D DGST_ELEM=4 -D KERN_TYPE=500 -D _unroll -cl-std=CL1.2'
Dictionary cache built:
* Filename..: /usr/share/wordlists/sqlmap.txt
* Passwords.: 1202867
* Bytes.....: 11004625
* Keyspace..: 1202867
* Runtime...: 1 sec

- Device #1: autotuned kernel-accel to 160
- Device #1: autotuned kernel-loops to 200
[s]tatus [p]ause [r]esume [b]ypass [c]heckpoint [q]uit => [s]tatus [p]ause [r]esume [b]ypass [c]heckpoint [q]uit => s

Session..........: hashcat
Status...........: Running
Hash.Type........: md5crypt, MD5 (Unix), Cisco-IOS $1$ (MD5)
Hash.Target......: $1$uOM6WNc4$r3ZGeSB11q6UUSILqek3J1
Time.Started.....: Thu Oct  5 14:14:17 2017 (40 secs)
Time.Estimated...: Thu Oct  5 14:15:47 2017 (50 secs)
Guess.Base.......: File (/usr/share/wordlists/sqlmap.txt)
Guess.Queue......: 1/1 (100.00%)
Speed.Dev.#1.....:    13205 H/s (9.58ms)
Recovered........: 0/1 (0.00%) Digests, 0/1 (0.00%) Salts
Progress.........: 531456/1202867 (44.18%)
Rejected.........: 256/531456 (0.05%)
Restore.Point....: 531456/1202867 (44.18%)
Candidates.#1....: e545o9rf7 -> e912013004
HWMon.Dev.#1.....: N/A

[s]tatus [p]ause [r]esume [b]ypass [c]heckpoint [q]uit =>
```

原文链接：https://tools.kali.org/password-attacks/hashcat

译者：[LaoK996](https://github.com/LaoK996)

校对：
