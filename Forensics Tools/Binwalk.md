---
title: Binwalk
categories: Forensics Tools
tags: [binwalk,forensics,kali linux]
date: 2017-09-07 07:15:00
---
0x00 Binwalk介绍
-------------
Binwalk是用于搜索给定二进制镜像文件以获取嵌入的文件和代码的工具。 具体来说，它被设计用于识别嵌入固件镜像内的文件和代码。 Binwalk使用libmagic库，因此它与Unix文件实用程序创建的魔数签名兼容。 Binwalk还包括一个自定义魔数签名文件，其中包含常见的诸如压缩/存档文件，固件头，Linux内核，引导加载程序，文件系统等的固件映像中常见文件的改进魔数签名。
<!--more-->

[主页][1] | [仓库][2]

 - 作者：Craig Heffner
 - 证书：MIT

0x01 功能
----------------
一个固件分析工具
```plain
root@kali:~# binwalk -h

Binwalk v2.1.1
Craig Heffner，http://www.binwalk.org

用法：binwalk [选项] [文件1] [文件2] [文件3] ...

扫描选项：
    -B，-- signature         扫描目标文件的常见文件签名
    -R，--raw = <str>        扫描目标文件的指定字符序列
    -A，--opcodes            扫描目标文件中常见可执行代码
    -m，--magic = <file>     指定要使用的自定义魔数签名文件
    -b，--dumb               禁用智能签名关键字
    -I，--invalid            显示结果标记为无效
    -x，--exclude = <str>    排除与<str>匹配的结果
    -y，--include = <str>    只显示匹配<str>的结果

提取选项：
    -e，--extract                  自动提取已知的文件类型
    -D，--dd = <type：ext：cmd>    提取<type>签名，为文件扩展名为<ext>，然后执行<cmd>
    -M，--matryoshka               递归扫描提取的文件
    -d，--depth = <int>            限制matryoshka递归深度（默认值：8级深）
    -C，--directory = <str>        将文件/文件夹提取到自定义目录（默认值：当前工作目录）
    -j，--size = <int>             限制每个提取的文件的大小
    -n，--count = <int>            限制提取文件的数量
    -r，--rm                       提取后删除刻录文件
    -z，--carve                    从文件中读取数据，但不执行提取实用程序

熵分析选项：
    -E，--entropy           计算文件熵
    -F，--fast              计算更快，但不太详细的熵分析
    -J，--save              将熵图保存为PNG图像
    -Q，--nlegend           从熵图图中省略图例
    -N，--nplot             不生成熵图
    -H，--high = <float>    设置上升沿熵触发阈值（默认值：0.95）
    -L，--low = <float>     设置下降沿熵触发阈值（默认值：0.85）

原始压缩选项：
    -X， --deflate          扫描原始deflate压缩流
    -Z， --lzma             扫描原始LZMA压缩流
    -P， --partial          浅度扫描，速度更快
    -S， --stop             找到第一个结果后停止扫描

二进制差异选项：
    -W，--hexdump           执行文件或文件的hexdump/diff
    -G，--green             只显示包含所有文件中相同字节的行
    -i，--red               仅显示包含所有文件中不同字节的行
    -U，--blue              只显示一些文件中包含不同字节的行
    -w，--terse             只显示第一个文件的十六进制转储

一般选项：
    -l，--length = <int>    要扫描的字节数
    -o，--offset = <int>    以此偏移开始扫描
    -O，--base = <int>      向所有打印的偏移量添加基址
    -K，--block = <int>     设置文件块大小
    -g，--swap = <int>      扫描前每n个字节反转一次
    -f，--log = <file>      将结果记录到文件
    -c，--csv               将结果记录到CSV格式的文件中
    -t，--term              格式化输出以适合终端窗口
    -q，--quiet             禁止输出
    -v，--verbose           详细输出
    -h，--help              显示帮助
    -a，--finclude = <str>  只扫描名称与此正则表达式匹配的文件
    -p，--fexclude = <str>  不扫描名称与此正则表达式匹配的文件
    -s，--status = <int>    启用指定端口上的状态服务器
```

0x02 用法示例
---------
在给定的固件文件（dd-wrt.v24-13064_VINT_mini.bin）上运行文件签名扫描（-B）：

```plain
root@kali:~# binwalk -B dd-wrt.v24-13064_VINT_mini.bin

DECIMAL     HEX         DESCRIPTION
-------------------------------------------------------------------------------------------------------------------
0           0x0         TRX firmware header, little endian, header size: 28 bytes, image size: 2945024 bytes, CRC32: 0x4D27FDC4 flags: 0x0, version: 1
28          0x1C        gzip compressed data, from Unix, NULL date: Wed Dec 31 19:00:00 1969, max compression
2472        0x9A8       LZMA compressed data, properties: 0x6E, dictionary size: 2097152 bytes, uncompressed size: 2084864 bytes
622592      0x98000     Squashfs filesystem, little endian, DD-WRT signature, version 3.0, size: 2320835 bytes,  547 inodes, blocksize: 131072 bytes, created: Mon Nov  2 07:24:06 2009
```

  [1]: http://binwalk.org/
  [2]: http://git.kali.org/gitweb/?p=packages/binwalk.git;a=summary