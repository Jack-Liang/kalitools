# theHarvester软件包描述

该程序的目标是收集来自于不同公开资源，如搜索引擎、PGP密钥服务器、SHODAN计算机数据库等的电子邮件、子域名、主机、员工姓名、开放端口和旗标信息。

旨在帮助渗透测试人员在渗透测试的早期阶段，了解客户在互联网上的足迹。这对任何想知道攻击者能看到自己组织是什么情况的人也是有用的。

这是一个完全重写的工具，引入了新的功能，如：

- 请求时间延迟
- 所有来源搜索
- 虚拟主机验证
- 活动枚举（DNS枚举、反向查找、TLD扩展）
- 集成SHODAN计算机数据库，获取开放端口和旗标信息
- 保存为XML和HTML
- 基础统计图
- 新的信息来源

资料来源：https://code.google.com/p/theharvester/

[theHarvester主页](https://code.google.com/p/theharvester/) | [Kali theHarvester资源](http://git.kali.org/gitweb/?p=packages/theharvester.git;a=summary)

- 作者：Christian Martorella
- 许可证：GPLv2

## theHarvester包含的工具
### theharvester - 从公开来源收集电子邮件帐户和子域名的工具
```
root@kali:~# theharvester

*******************************************************************
*                                                                 *
* | |_| |__   ___    /\  /\__ _ _ ____   _____  ___| |_ ___ _ __  *
* | __| '_ \ / _ \  / /_/ / _` | '__\ \ / / _ \/ __| __/ _ \ '__| *
* | |_| | | |  __/ / __  / (_| | |   \ V /  __/\__ \ ||  __/ |    *
*  \__|_| |_|\___| \/ /_/ \__,_|_|    \_/ \___||___/\__\___|_|    *
*                                                                 *
* TheHarvester Ver. 2.2a                                          *
* Coded by Christian Martorella                                   *
* Edge-Security Research                                          *
* cmartorella@edge-security.com                                   *
*******************************************************************

用法：theharvester 选项

        -d：搜索的域或公司名称
        -b：数据来源（google、bing、bingapi、pgp、linkedin、google-profiles、baidu、jigsaw、all）
        -s：结果编号从X开始（默认为0）
        -v：通过dns解析验证主机名，并搜索虚拟主机
        -f：将结果保存到HTML和XML文件中
        -n：对所有发现的地址范围进行DNS反向查询
        -c：对域名执行DNS强力解析
        -t：执行DNS TLD扩展发现
        -e：指定DNS服务器
        -l：限制结果数量（pgp不使用此选项）
        -h：使用SHODAN数据库查询已发现的主机
             

例子:    theharvester -d microsoft.com -l 500 -b google
        theharvester -d microsoft.com -b pgp
        theharvester -d microsoft -l 200 -b linkedin
```
## theharvester使用示例

从域（-d kali.org）搜索电子邮件地址，使用Google（-b google）将结果限制为500（-l 500）：
```
root@kali:~# theharvester -d kali.org -l 500 -b google

*******************************************************************
*                                                                 *
* | |_| |__   ___    /\  /\__ _ _ ____   _____  ___| |_ ___ _ __  *
* | __| '_ \ / _ \  / /_/ / _` | '__\ \ / / _ \/ __| __/ _ \ '__| *
* | |_| | | |  __/ / __  / (_| | |   \ V /  __/\__ \ ||  __/ |    *
*  \__|_| |_|\___| \/ /_/ \__,_|_|    \_/ \___||___/\__\___|_|    *
*                                                                 *
* TheHarvester Ver. 2.2a                                          *
* Coded by Christian Martorella                                   *
* Edge-Security Research                                          *
* cmartorella@edge-security.com                                   *
*******************************************************************


[-] Searching in Google:
        Searching 0 results...
        Searching 100 results...
        Searching 200 results...
        Searching 300 results...
        Searching 400 results...
        Searching 500 results...
```

原文链接：[http://tools.kali.org/information-gathering/theharvester](http://tools.kali.org/information-gathering/theharvester)
