# dnsmap

## dnsmap包

dnsmap最初于2006年发布，并受到Paul Craig的科幻故事“The Thief No One Saw”的启发，这个故事可以在“Stealing the Network – How to 0wn the Box”一书中找到。

dnsmap主要用于在基础设施安全评估的信息收集/枚举阶段期间由攻击者使用。 在枚举阶段，通常会发现目标公司的IP网段，域名，电话号码等...

子域强制是在枚举阶段应该使用的另一种技术，因为它在其他域枚举技术，比如区域传输，不起作用时尤其有用（我很少看到区域传输在这些日子被公开允许）。



**来源**: http://code.google.com/p/dnsmap/
[dnsmap Homepage](http://code.google.com/p/dnsmap/) | [Kali dnsmap Repo](http://git.kali.org/gitweb/?p=packages/dnsmap.git;a=summary)

- 作者: pagvcac

- 许可证: GPLv2

  ​

## dnsmap包中包含的工具:

### dnsmap - DNS域名暴力破解工具

```
root@kali:~# dnsmap
dnsmap 0.30 - DNS Network Mapper by pagvac (gnucitizen.org)

usage: dnsmap <target-domain> [options]
options:
-w <wordlist-file>
-r <regular-results-file>
-c <csv-results-file>
-d <delay-millisecs>
-i <ips-to-ignore> (useful if you're obtaining false positives)

e.g.:
dnsmap target-domain.foo
dnsmap target-domain.foo -w yourwordlist.txt -r /tmp/domainbf_results.txt
dnsmap target-fomain.foo -r /tmp/ -d 3000
dnsmap target-fomain.foo -r ./domainbf_results.txt
```

### dnsmap-bulk.sh - DNS域名暴力破解工具

```
root@kali:~# dnsmap-bulk.sh
usage: dnsmap-bulk.sh <domains-file> [results-path]
e.g.:
dnsmap-bulk.sh domains.txt
dnsmap-bulk.sh domains.txt /tmp/
```

## dnsmap用法示例

### dnsmap用法示例

用单词表(**-w /usr/share/wordlists/dnsmap.txt**)扫描目标网站 **example.com** 

```
root@kali:~# dnsmap example.com -w /usr/share/wordlists/dnsmap.txt
dnsmap 0.30 - DNS Network Mapper by pagvac (gnucitizen.org)

[+] searching (sub)domains for example.com using /usr/share/wordlists/dnsmap.txt
[+] using maximum random delay of 10 millisecond(s) between requests
```



### dnsmap-bulk用法示例

创建包含要扫描的域名的文件（**domains.txt**）并把它传递给dnsmap-bulk.sh:

```
root@kali:~# echo "example.com" >> domains.txt
root@kali:~# echo "example.org" >> domains.txt
root@kali:~# dnsmap-bulk.sh domains.txt
dnsmap 0.30 - DNS Network Mapper by pagvac (gnucitizen.org)

[+] searching (sub)domains for example.com using built-in wordlist
[+] using maximum random delay of 10 millisecond(s) between requests
```

原文链接: http://tools.kali.org/information-gathering/dnsmap

