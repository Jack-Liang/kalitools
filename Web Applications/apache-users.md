# apache-users包说明

这个Perl脚本程序会列出所有使用Apache UserDir模块中的用户名

[apache-users首页](https://labs.portcullis.co.uk/) | [Kali apache-users仓库](http://git.kali.org/gitweb/?p=packages/apache-users.git;a=summary)

作者: Andy@Portcullis

协议: GPLv2

apache-users包中的工具

apache-users – 列举在Apache UserDir模块中的用户名

```
root@kali:~# apache-users

USAGE: apache.pl [-h 1.2.3.4] [-l names] [-p 80] [-s (SSL Support 1=true 0=false)] [-e 403 (http code)] [-t threads]
```

# apache-users使用范例

分析远程主机 (-h 192.168.1.202), 传送有用户名的目录 (-l /usr/share/wordlists/metasploit/unix_users.txt),监听端口 (-p 80), 不使用SSL (-s 0), 指明HTTP状态码 (-e 403), 使用10个线程 (-t 10):

```
root@kali:~# apache-users -h 192.168.1.202 -l /usr/share/wordlists/metasploit/unix_users.txt -p 80 -s 0 -e 403 -t 10
```
