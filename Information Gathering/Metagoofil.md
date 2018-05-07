---
title: Metagoofil
categories: Information Gathering
tags: [information gathering,kali linux,recon,enumeration,reporting,metagoofil]
date: 2017-04-24 13:01:00
---
0x00 介绍
-------
Metagoofil是一种搜索提取目标公司公开文档（pdf，doc，xls，ppt，docx，pptx，xlsx）中元数据的信息收集工具。

Metagoofil将在Google中进行搜索，以将文档识别并下载到本地磁盘，然后将使用不同的库（如Hachoir，PdfMiner）提取元数据，通过分析得到结果生成具有用户名，软件版本和服务器或机器名称的报告，有助于渗透测试人员信息收集阶段的工作。

“MetaGooFil”也是信息收集过程中可以利用的优秀软件，由开发The Harvester的团队编写而成，可用来提取元数据（metadata）。元数据经常被定义为是关于数据的数据。在我们创建文档时，例如Word或PowerPoint演示文稿，额外的数据也会被同时创建，并储存在文档里。这些数据通常是对该文档的描述信息，包括文件名、文件大小、作者或创建者的用户名，以及文件保存的位置或路径。这个过程全自动进行，无需用户输入或干预。

攻击者若能读取到这些信息，就能对目标公司的用户名、系统名、文件共享以及其他诸多好东西有独特的见解。MetaGooFil就是这么一个工具，能在互联网上搜索属于目标的文档。一旦有所发现，MetaGooFil就会把这些文档下载下来，并尝试提取有用的元数据。

<!--more-->

[主页][1] | [仓库][2]

 - 作者：Christian Martorella
 - 证书：GPLv2

0x01 功能
-------
metagoofil - 用于提取公共文档元数据的工具
```
root@kali:~# metagoofil

******************************************************
*     /\/\   ___| |_ __ _  __ _  ___   ___  / _(_) | *
*    /    \ / _ \ __/ _` |/ _` |/ _ \ / _ \| |_| | | *
*   / /\/\ \  __/ || (_| | (_| | (_) | (_) |  _| | | *
*   \/    \/\___|\__\__,_|\__, |\___/ \___/|_| |_|_| *
*                         |___/                      *
* Metagoofil Ver 2.2                                 *
* Christian Martorella                               *
* Edge-Security.com                                  *
* cmartorella_at_edge-security.com                   *
******************************************************

 用法: metagoofil [选项]

         -d: 目标域名
         -t: 下载文件的类型 (pdf,doc,xls,ppt,odp,ods,docx,xlsx,pptx)
         -l: 限制搜索结果数量 (默认 200)
         -h: 分析目录中的文档 (值为"yes"进行本地分析)
         -n: 限制下载文件数量
         -o: 工作目录 (保存下载文件目录)
         -f: 输出文件

 示例:
  metagoofil.py -d apple.com -t doc,pdf -l 200 -n 50 -o applefiles -f results.html
  metagoofil.py -h yes -o applefiles -f results.html (本地目录分析)
```
0x02 示例
-------
搜索PDF文件（-t pdf），搜索100个结果（-l 100），下载25个文件（-n 25），目标域（-d kali.org）中的文档，将下载保存到目录（-o kalipdf），并将输出保存到文件（-f kalipdf.html）：
```
root@kali:~# metagoofil -d kali.org -t pdf -l 100 -n 25 -o kalipdf -f kalipdf.html

******************************************************
*     /\/\   ___| |_ __ _  __ _  ___   ___  / _(_) | *
*    /    \ / _ \ __/ _` |/ _` |/ _ \ / _ \| |_| | | *
*   / /\/\ \  __/ || (_| | (_| | (_) | (_) |  _| | | *
*   \/    \/\___|\__\__,_|\__, |\___/ \___/|_| |_|_| *
*                         |___/                      *
* Metagoofil Ver 2.2                                 *
* Christian Martorella                               *
* Edge-Security.com                                  *
* cmartorella_at_edge-security.com                   *
******************************************************
['pdf']

[-] Starting online search...

[-] Searching for pdf files, with a limit of 100
        Searching 100 results...
Results: 21 files found
Starting to download 25 of them:
```


  [1]: http://www.edge-security.com/metagoofil.php
  [2]: http://git.kali.org/gitweb/?p=packages/metagoofil.git;a=summary