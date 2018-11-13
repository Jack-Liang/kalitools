#John the Ripper

##John 包描述

John the Ripper 既功能丰富又运行快速。 它在一个程序中结合了几种破解模式，并且可以根据您的特定需求进行全面地配置（你甚至可以使用支持C的子集的内置编译器来设计一个自定义的破解模式）。 此外，John可以使用几种不同的平台，使您能够在任何地方使用相同的破解方法（您甚至可以继续进行已经在另一个平台上启动的破解会话）。

革新的是，John 支持（并自动检测）以下 Unix crypt（3）散列类型：基于DES的传统类型，“bigcrypt”，基于DES扩展的BSDI，基于MD5的FreeBSD（也用于Linux和Cisco IOS） 和基于Blowfish的OpenBSD（现在也在某些Linux发行版上使用，并且受Solaris的最新版本的支持），另外，还革新地支持Kerberos / AFS和Windows LM（基于DES）的散列，以及基于DES的跳码。

当在具有glibc 2.7+的Linux发行版上运行时，借助可选的OpenMP并行化（需要GCC 4.2+，需要在编译时通过取消注释Makefile附近的正确的OMPFLAGS行来显式启用），John 1.7.6+还支持（和自动检测）SHA-crypt哈希值（实际上由Fedora和Ubuntu的最新版本使用）。

同样，当运行在最新版本的Solaris上时，John 1.7.6+支持并自动检测SHA-crypt和SunMD5散列，并且还可以使用可选的OpenMP并行化（需要GCC 4.2+或最近的Sun Studio，需要在编译时通过 对Makefile开头附近对应的OMPFLAGS行取消注释，并在运行时将OMP_NUM_THREADS环境变量设置为所需的线程数的方式 来显式启用）。

John Ripper Pro增加了对Windows NTLM（基于MD4）和Mac OS X 10.4+盐化SHA-1散列的支持。

“社区增强”-jumbo版本增加了许多更多密码散列类型的支持，包括Windows NTLM（基于MD4），Mac OS X 10.4-10.6盐化SHA-1散列，Mac OS X 10.7盐化SHA-512散列，原始MD5和 SHA-1，任意的基于MD5的“Web应用程序”密码哈希类型，SQL数据库服务器（MySQL，MS SQL，Oracle）和某些LDAP服务器使用的哈希值，OpenVMS上使用的几种哈希类型，Eggdrop IRC bot的密码哈希 ，以及许多其他散列类型，以及诸如OpenSSH私钥，S / Key skeykeys文件，Kerberos TGT，PDF文件，ZIP（经典PKZIP和WinZip / AES）和RAR存档之类的许多非散列。

与旧的破解工具不同，John通常不会使用crypt（3）风格的例程。 相反，它有自己的高度优化的模块，用于不同的哈希类型和处理器架构。 使用的一些算法，如位图DES，不能在crypt（3）API中实现; 他们需要一个更强大的界面，如John中使用的界面。 此外，还有几种处理器架构的汇编语言程序，最重要的是x86-64和x86 with SSE2。

资料来源：http://www.openwall.com/john/doc/

[John the Ripper主页](http://www.openwall.com/john/)|[Kali John the Ripper仓库](http://git.kali.org/gitweb/?p=packages/john.git;a=summary)

-作者：Solar Designer
-许可证：GPLv2

##John 包中包含的工具
###mailer - 给密码被破解的用户发送电子邮件
```
root@kali:~# mailer
Usage: /usr/sbin/mailer PASSWORD-FILE
```

##john - John the Ripper密码破解器
```
root@kali:~# john
John the Ripper password cracker, ver: 1.7.9-jumbo-7_omp [linux-x86-sse2]
Copyright (c) 1996-2012 by Solar Designer and others
Homepage: http://www.openwall.com/john/

Usage: john [OPTIONS] [PASSWORD-FILES]
--config=FILE             use FILE instead of john.conf or john.ini
--single[=SECTION]        "single crack" mode
--wordlist[=FILE] --stdin wordlist mode, read words from FILE or stdin
                  --pipe  like --stdin, but bulk reads, and allows rules
--loopback[=FILE]         like --wordlist, but fetch words from a .pot file
--dupe-suppression        suppress all dupes in wordlist (and force preload)
--encoding=NAME           input data is non-ascii (eg. UTF-8, ISO-8859-1).
                          For a full list of NAME use --list=encodings
--rules[=SECTION]         enable word mangling rules for wordlist modes
--incremental[=MODE]      "incremental" mode [using section MODE]
--markov[=OPTIONS]        "Markov" mode (see doc/MARKOV)
--external=MODE           external mode or word filter
--stdout[=LENGTH]         just output candidate passwords [cut at LENGTH]
--restore[=NAME]          restore an interrupted session [called NAME]
--session=NAME            give a new session the NAME
--status[=NAME]           print status of a session [called NAME]
--make-charset=FILE       make a charset file. It will be overwritten
--show[=LEFT]             show cracked passwords [if =LEFT, then uncracked]
--test[=TIME]             run tests and benchmarks for TIME seconds each
--users=[-]LOGIN|UID[,..] [do not] load this (these) user(s) only
--groups=[-]GID[,..]      load users [not] of this (these) group(s) only
--shells=[-]SHELL[,..]    load users with[out] this (these) shell(s) only
--salts=[-]COUNT[:MAX]    load salts with[out] COUNT [to MAX] hashes
--pot=NAME                pot file to use
--format=NAME             force hash type NAME: afs bf bfegg bsdi crc32 crypt
                          des django dmd5 dominosec dragonfly3-32 dragonfly3-64
                          dragonfly4-32 dragonfly4-64 drupal7 dummy dynamic_n
                          epi episerver gost hdaa hmac-md5 hmac-sha1
                          hmac-sha224 hmac-sha256 hmac-sha384 hmac-sha512
                          hmailserver ipb2 keepass keychain krb4 krb5 lm lotus5
                          md4-gen md5 md5ns mediawiki mscash mscash2 mschapv2
                          mskrb5 mssql mssql05 mysql mysql-sha1 nethalflm netlm
                          netlmv2 netntlm netntlmv2 nsldap nt nt2 odf office
                          oracle oracle11 osc pdf phpass phps pix-md5 pkzip po
                          pwsafe racf rar raw-md4 raw-md5 raw-md5u raw-sha
                          raw-sha1 raw-sha1-linkedin raw-sha1-ng raw-sha224
                          raw-sha256 raw-sha384 raw-sha512 salted-sha1 sapb
                          sapg sha1-gen sha256crypt sha512crypt sip ssh
                          sybasease trip vnc wbb3 wpapsk xsha xsha512 zip
--list=WHAT               list capabilities, see --list=help or doc/OPTIONS
--save-memory=LEVEL       enable memory saving, at LEVEL 1..3
--mem-file-size=SIZE      size threshold for wordlist preload (default 5 MB)
--nolog                   disables creation and writing to john.log file
--crack-status            emit a status line whenever a password is cracked
--max-run-time=N          gracefully exit after this many seconds
--regen-lost-salts=N      regenerate lost salts (see doc/OPTIONS)
--plugin=NAME[,..]        load this (these) dynamic plugin(s)
```

##unafs - 对用户弱口令进行警告的脚本
```
root@kali:~# unafs
Usage: unafs DATABASE-FILE CELL-NAME
```

##unshadow - 结合passwd和shadow文件
```
root@kali:~# unshadow
Usage: unshadow PASSWORD-FILE SHADOW-FILE
```

##unique - 从单词列表中删除重复项
```
root@kali:~# unique
Usage: unique [-v] [-inp=fname] [-cut=len] [-mem=num] OUTPUT-FILE [-ex_file=FNAME2] [-ex_file_only=FNAME2]

       reads from stdin 'normally', but can be overridden by optional -inp=
       If -ex_file=XX is used, then data from file XX is also used to
       unique the data, but nothing is ever written to XX. Thus, any data in
       XX, will NOT output into OUTPUT-FILE (for making iterative dictionaries)
       -ex_file_only=XX assumes the file is 'unique', and only checks against XX
       -cut=len  Will trim each input lines to 'len' bytes long, prior to running
       the unique algorithm. The 'trimming' is done on any -ex_file[_only] file
       -mem=num.  A number that overrides the UNIQUE_HASH_LOG value from within
       params.h.  The default is 21.  This can be raised, up to 25 (memory usage
       doubles each number).  If you go TOO large, unique will swap and thrash and
       work VERY slow

       -v is for 'verbose' mode, outputs line counts during the run
       ```
       
##unshadow 使用示例

结合提供的passwd*(passwd)*和shadow*(shadow)*(shadow)并将它们重定向到一个文件*(> unshadowed.txt)*：
```
root@kali:~# unshadow passwd shadow > unshadowed.txt
```

##john 使用示例

使用一张单词列表*(-wordlist = /usr/share/john/password.lst)*，应用修改的规则*(-rules)*并尝试破解给定文件*(unshadowed.txt)*中的密码散列：
```
root@kali:~# john --wordlist=/usr/share/john/password.lst --rules unshadowed.txt
Warning: detected hash type "sha512crypt", but the string is also recognized as "crypt"
Use the "--format=crypt" option to force loading these as that type instead
Loaded 1 password hash (sha512crypt [64/64])
toor             (root)
guesses: 1  time: 0:00:00:07 DONE (Mon May 19 08:13:05 2014)  c/s: 482  trying: 1701d - andrew
Use the "--show" option to display all of the cracked passwords reliably
```

##unique使用示例

使用详细模*(-v)*，读取密码列表*(-inp = allwords.txt)*，并只将唯一的单词保存到文件*(uniques.txt)*中：
```
root@kali:~# unique -v -inp=allwords.txt uniques.txt
Total lines read 6089 Unique lines written 5083
```

@(标签)[passwords](http://tools.kali.org/tag/passwords)
***
##相关文章

[gpp-decrypt](http://tools.kali.org/password-attacks/gpp-decrypt)
[WebScarab](http://tools.kali.org/web-applications/webscarab)
[TrueCrack](http://tools.kali.org/password-attacks/truecrack)
