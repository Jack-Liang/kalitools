---
title: goofile
categories: Information Gathering
tags: [information gathering,goofile,kali linux]
date: 2017-04-23 06:24:00
---
0x00 goofile介绍
-------------
视频介绍：[https://asciinema.org/a/31264][1]
使用此工具可以在给定的域中搜索特定的文件类型。


<!--more-->


[goofile主页][2] | [Kali goofile仓库][3]

 - 作者：Thomas Richards
 - 证书：MIT

0x01 goofile功能
----------------

golismero - Web应用程序映射器
```plain
root@kali:~# goofile

-------------------------------------
|Goofile v1.5                       |
|Coded by Thomas (G13) Richards     |
|www.g13net.com                     |
|code.google.com/p/goofile          |
-------------------------------------


Goofile 1.5

用法: goofile [选项]

       -d: 指定域名

       -f: 指定文件类型 (扩展名如：pdf)

示例:./goofile.py -d test.com -f txt
```

0x02 goofile用法示例
-----------------
搜索域名(-d kali.org)中的PDF文件(-f pdf):
```shell
root@kali:~# goofile -d kali.org -f pdf

-------------------------------------
|Goofile v1.5                       |
|Coded by Thomas (G13) Richards     |
|www.g13net.com                     |
|code.google.com/p/goofile          |
-------------------------------------


Searching in kali.org for pdf
========================================

Files found:
====================

docs.kali.org/pdf/kali-book-fr.pdf
docs.kali.org/pdf/kali-book-es.pdf
docs.kali.org/pdf/kali-book-id.pdf
docs.kali.org/pdf/kali-book-de.pdf
docs.kali.org/pdf/kali-book-it.pdf
docs.kali.org/pdf/kali-book-ar.pdf
docs.kali.org/pdf/kali-book-ja.pdf
docs.kali.org/pdf/kali-book-nl.pdf
docs.kali.org/pdf/kali-book-ru.pdf
docs.kali.org/pdf/kali-book-en.pdf
docs.kali.org/pdf/kali-book-pt-br.pdf
docs.kali.org/pdf/kali-book-zh-hans.pdf
docs.kali.org/pdf/kali-book-sw.pdf
docs.kali.org/pdf/articles/kali-linux-live-usb-install-en.pdf
====================
```

  [1]: https://asciinema.org/a/31264
  [2]: http://code.google.com/p/goofile/
  [3]: http://git.kali.org/gitweb/?p=packages/goofile.git;a=summary