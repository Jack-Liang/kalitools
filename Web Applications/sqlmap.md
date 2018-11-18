# sqlmap软件包描述

sqlmap是一个开源的渗透测试工具，它可以自动化检测和利用SQL注入漏洞并接管数据库服务器。它有一个强大的检测引擎，许多适合于终极渗透测试的良好特性和众多的操作选项，从数据库指纹、数据获取到访问底层文件系统、执行操作系统命令。

特点:

- 全面支持MySQL, Oracle, PostgreSQL, Microsoft SQL Server, Microsoft Access, IBM DB2, SQLite, Firebird, Sybase和SAP MaxDB数据库管理系统。
- 全面支持六种SQL注入技术:boolean-based盲注、time-based盲注、error-based、UNION查询、堆叠查询和带外查询。
- 通过提供DBMS凭证、IP地址、端口和数据库名，支持不通过SQL注入的直接连接数据库。
- 支持枚举用户、密码哈希、特权、角色、数据库、表和列。
- 自动识别密码哈希格式，支持基于字典的攻击破解。
- 支持完整转储数据库表，根据用户的选择转储一定范围内的条目或特定列。用户还可以选择只从每列中转储指定字符。
- 支持搜索特定的数据库名、表名，或跨表搜索特定的列名。这非常有用，例如，识别包含自定义应用程序凭证的表，其相关列名称可能包含name、pass等字符串。
- 支持通过数据库服务器所在的文件系统下载和上传任何文件，当数据库软件是MySQL, PostgreSQL或Microsoft SQL server时。
- 支持通过数据库服务器所在的操作系统执行任意命令并获取输出，当数据库软件为MySQL、PostgreSQL或Microsoft SQL server时。
- 支持在攻击者机器和数据库服务器所在操作系统之间建立带外有状态的TCP连接，这个通道根据用户的选择可以是交互式命令行、Meterpreter会话或图形用户界面(VNC)。
- 支持通过Metasploit的getsystem命令实现数据库进程的用户权限升级。

资料来源:http://sqlmap.org/

[sqlmap主页](http://sqlmap.org/) | [Kali sqlmap软件源](http://git.kali.org/gitweb/?p=packages/sqlmap.git;a=summary)

- 作者:Bernardo Damele Assumpcao Guimaraes, Miroslav Stampar
- 许可:GPLv2

## sqlmap包中包含的工具
### sqlmap -自动SQL注入工具
```
root@kali:~# sqlmap -h
Usage: python sqlmap [options]

Options:
  -h, --help            显示基本的帮助信息并退出
  -hh                   显示高级帮助信息并退出
  --version             显示程序的版本号并退出
  -v VERBOSE            显示详细信息级别: 0-6 (default 1)

  Target:
    至少必须提供一个选项来指定目标

    -u URL, --url=URL   目标URL (e.g. "http://www.site.com/vuln.php?id=1")
    -g GOOGLEDORK       将Google dork结果作为目标URLs

  Request:
    这些选项用于指定如何连接到目标URL

    --data=DATA         通过POST方法传送字符串
    --cookie=COOKIE     指定HTTP Cookie值
    --random-agent      随机选择HTTP User-Agent值
    --proxy=PROXY       指定连接代理
    --tor               使用Tor匿名网络
    --check-tor         检查Tor网络是否可用

  Injection:
    这些选项可用于指定要测试的参数，提供自定义注入载荷和可选的伪造脚本

    -p TESTPARAMETER    Testable参数
    --dbms=DBMS         强制指定后端DBMS类型

  Detection:
    这些选项可用于定制检测阶段

    --level=LEVEL       Level of tests to perform (1-5, default 1)
    --risk=RISK         Risk of tests to perform (0-3, default 1)

  Techniques:
    这项选项可用于优化特定的SQL注入技巧

    --technique=TECH    SQL injection techniques to use (default "BEUSTQ")

  Enumeration:
    这些选项可用于枚举后端数据库管理系统中包含的信息、结构和数据表。此外，还可以运行自己的SQL语句

    -a, --all           获取所有信息
    -b, --banner        获取DBMS banner
    --current-user      获取DBMS当前用户
    --current-db        获取DBMS当前数据库
    --passwords         枚举DBMS用户口令哈希
    --tables            枚举DBMS数据库表
    --columns           枚举DBMS数据表的列
    --schema            枚举DBMS schema
    --dump              转储DBMS database table entries
    --dump-all          转储所有DBMS databases tables entries
    -D DB               指定DBMS数据库
    -T TBL              指定DBMS数据表
    -C COL              指定DBMS数据表的列

  Operating system access:
    这些选项可用于访问后端数据库管理系统所在的底层操作系统

    --os-shell          启动交互式操作系统命令行
    --os-pwn            启动OOB shell, Meterpreter or VNC

  General:
    这些选项可用于设置通用参数

    --batch             不要求用户输入，使用默认值
    --flush-session     对当前目标刷新会话文件

  Miscellaneous:
    --wizard            适用于初学者的简单向导

[!] 完整的选项信息可使用'-hh'获取

[*] shutting down at 15:52:48
```
### sqlmap使用示例

攻击给定的URL(-u “http://192.168.1.250/?p=1&forumaction=search”)， 获取数据库名(–dbs):
```
root@kali:~# sqlmap -u "http://192.168.1.250/?p=1&forumaction=search" --dbs

    sqlmap/1.0-dev - automatic SQL injection and database takeover tool
    http://sqlmap.org

[!] legal disclaimer: Usage of sqlmap for attacking targets without prior mutual consent is illegal. It is the end user's responsibility to obey all applicable local, state and federal laws. Developers assume no liability and are not responsible for any misuse or damage caused by this program

[*] starting at 13:11:04

```

原文链接：https://tools.kali.org/vulnerability-analysis/sqlmap

译者：[LaoK996](https://github.com/LaoK996)

校对：
