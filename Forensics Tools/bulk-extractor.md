---
title: bulk-extractor
categories: Forensics Tools
tags: [forensics,kali linux,bulk-extractor]
date: 2017-09-07 09:22:00
---
0x00 介绍
-------------
bulk_extractor是从数字证据文件中提取诸如电子邮件地址，信用卡号，URL和其他类型的信息的功能的程序。 它是一个有用的取证调查工具，可以用于许多任务，如恶意软件和入侵调查，身份调查和网络调查，以及图像分析和密码破解。 该程序提供了几个不寻常的功能：

     1.发现其他工具发现不了的信息，如电子邮件地址，URL和信用卡号码，得益于它能处理压缩数据（如ZIP，PDF和GZIP文件）以及不完整或部分损坏的数据。 它可以从压缩数据的片段中提取JPEG文件，办公文档和其他类型的文件 ，还可以自动检测并提取加密的RAR文件。
     2.根据数据中发现的所有单词构建单词列表，甚至可以是在未分配空间的压缩文件中的数据。 这些单词列表可用于密码破解。
     3.多线程的; 速度快节约时间
     4.分析完之后创建直方图，显示电子邮件地址，URL，域名，搜索关键词和其他类型的信息。

bulk_extractor可以对磁盘映像，文件或文件目录进行分析，并在不分析文件系统或文件系统结构的情况下提取有用的信息。 输入被分割成页面并由一个或多个扫描器处理。 结果存储在特征文件中，可以使用其他自动化工具轻松检查，解析或处理。
bulk_extractor还创建了它所发现的特征的直方图。 这样非常有用，因为诸如电子邮件地址和网络搜索关键词的功能往往很常见且重要。
除了上述功能之外，bulk_extractor还包括以下功能：

     5.具有浏览特征文件中存储的功能以及启动bulk_extractor扫描的图形用户界面的Bulk Extractor Viewer
     6.少量用于对特征文件进行额外分析的python程序
<!--more-->

来源：[http://digitalcorpora.org/downloads/bulk_extractor/BEUsersManual.pdf][1]
[主页][2] | [仓库][3]

 - 作者：Simson L. Garfinkel
 - 证书：GPLv2

0x01 功能
----------------
bulk_extractor - 在不解析文件系统的情况下提取信息。
```plain
bulk_extractor version 1.6.0-dev
用法：bulk_extractor [选项] 文件
运行bulk_extractor并提取摘要信息并输出到文件

必需参数：
   imagefile     - 要提取的文件
或者-R filedir   - 遍历目录下的文件
                  支持E01文件
                  支持AFF文件
   -o outdir     - 指定输出目录，目录不得已存在
                  bulk_extractor将创建此目录
选项：
   -i                 - 信息模式。快速分析随机取样的样本并打印报告
   -b banner.txt      - 将banner.txt内容添加到每个输出文件的头部
   -r alert_list.txt  - 包含提醒作业的警报列表的文件
                       （可以是特征文件或全局列表）
                       （可以重复）
   -w stop_list.txt   - 包含功能停止列表的文件（白名单）
                       （可以是特征文件或全局列表）
                       （可以重复）
   -F <rfile>         - 从<rfile>读取正则表达式列表以查找
   -f <regex>         - 查找出现的<regex>;可能重复。
                        结果存入find.txt
   -q nn              - 静默的模式;只输出nn级别的状态报告。默认值0; -1，没有状态输出
   -s frac [：passes] - 设置随机抽样参数

调整参数：
   -C NN                            - 指定上下文窗口的大小（默认值为16）
   -S fr:<name>:window = NN         - 指定录像机到NN的上下文窗口
   -S fr:<name>:window_before = NN  - 指定之前的上下文窗口到NN为记录器
   -S fr:<name>:window_after = NN   - 指定后缀到NN后的上下文窗口
   -G NN                            - 指定页面大小（默认16777216）
   -g NN                            - 指定余量（默认4194304）
   -j NN                            - 要运行的分析线程数（默认4）
   -M nn                            - 设置最大递归深度（默认7）
   -m <max>                         - 所有数据读取后等待的最大分钟数（默认60）

路径处理模式：
   -p <path> / f - 以给定的格式打印<path>的值。
                  格式：r = 源格式; h = 十六进制格式。
                  指定-p - 进行交互模式
                  指定-p -http为HTTP模式

并行化：
   -Y <o1>        - 在o1开始处理（o1可以是1，1K，1M或1G）
   -Y <o1> - <o2> - 处理o1-o2
   -A <off>       - 将<off>添加到所有报告的特征偏移

调试：
   -h     - 打印此消息
   -H     - 打印扫描仪的详细信息
   -V     - 打印版本号
   -z nn  - 从第nn页开始
   -dN    - 调试模式（参见源代码）
   -Z     - 清除输出目录

扫描控制：
   -P <dir>       - 指定一个插件目录
                    默认目录包括/usr/local/lib/bulk_extractor，/usr/lib/bulk_extractor和
                    BE_PATH环境变量
   -e <scanner>     启用扫描器 - -e all   全部启用
   -x <scanner>     禁用扫描器 - -x all   全部禁用
   -E <scanner>   - 关闭除指定扫描器以外的所有扫描器
                   （与-x all -e <scanner>效果一样）
                    注意：-e，-x和-E命令按顺序执行
                    例如：'-E gzip -e facebook'只运行gzip和facebook
   -S name = value - 将批量提取器选项名称设置为值


可设置选项（及其默认值）：
   -S work_start_work_end = YES                   在report.xml文件中记录每个扫描器的工作开始和结束时间
   -S enable_histograms = YES                     禁用生成直方图
   -S debug_histogram_malloc_fail_frequency = 0   设置大于零记录内存分配失败直方图
   -S hash_alg = md5                              指定用于所有哈希计算的哈希算法
   -S dup_data_alerts =NO                         重复数据未处理时通知
   -S write_feature_files = YES                   写入特征文件
   -S write_feature_sqlite3 = NO                  将特征文件写入report.sqlite3
   -S report_read_errors = YES                    报告读取错误
   -S carve_net_memory = NO                       提取网络内存结构（net）
   -S word_min = 6                                最小字大小（wordlist）
   -S word_max = 14                               最大字大小（wordlist）
   -S max_word_outfile_size = 100000000           输出文件的最大大小（wordlist）
   -S wordlist_use_flatfiles = YES                覆盖SQL设置并对wordlist（wordlist）使用flatfiles
   -S ssn_mode = 0                                0=正常格式; 1=不需要SSN; 2=去掉破折号（accts）
   -S min_phone_digits = 7                        手机所需的数字（accts）
   -S exif_debug = 0                              读取exif信息（exif）
   -S jpeg_carve_mode = 1                         0=不提取; 1=雕刻编码提取; 2=全部提取（exif）
   -S min_jpeg_size = 1000                        将被雕刻的最小的JPEG流（exif）
   -S zip_min_uncompr_size = 6                    ZIP未压缩对象的最小大小（zip）
   -S zip_max_uncompr_size = 268435456            ZIP未压缩对象的最大大小（zip）
   -S zip_name_len_max = 1024                     ZIP组件的最大名称filename（zip）
   -S unzip_carve_mode = 1                        0=不提取; 1=雕刻编码提取; 2=全部提取（zip）
   -S rar_find_components = YES                   搜索RAR组件（rar）
   -S rar_find_volumes = YES                      搜索RAR卷（rar）
   -S unrar_carve_mode = 1                        0=不提取; 1=雕刻编码提取; 2=全部提取（rar）
   -S gzip_max_uncompr_size = 268435456           解压缩GZIP对象的最大大小（gzip）
   -S pdf_dump = NO                               转储PDF缓冲区的内容（pdf）
   -S pdf_dump = NO                               转储PDF缓冲区的内容（msxml）
   -S winpe_carve_mode = 1                        0=不提取; 1=雕刻编码提取; 2=全部提取（winpe）
   -S opt_weird_file_size = 157286400             FAT32扫描（windir）的阈值
   -S opt_weird_file_size2 = 536870912            FAT32扫描（windir）的阈值
   -S opt_weird_cluster_count = 67108864          FAT32扫描（windir）的阈值
   -S opt_weird_cluster_count2 = 268435456        FAT32扫描（windir）的阈值
   -S opt_max_bits_in_attrib = 3                  忽略更多属性设置的FAT32条目（windirs）
   -S opt_max_weird_count = 2                     忽略奇怪的FAT32条目（windirs）
   -S opt_last_year = 2022                        忽略晚于此FAT32条目（windirs）
   -S xor_mask = 255                              设置XOR掩码值，十进制格式（xor）
   -S sqlite_carve_mode = 2                       0=不提取; 1=雕刻编码提取; 2=全部提取（sqlite）

以下扫描默认禁用;启用使用-e命令：
   -e base16   - 启用扫描base16
   -e facebook - 启用扫描facebook
   -e outlook  - 启用扫描outlook
   -e sceadan  - 启用扫描sceadan
   -e wordlist - 启用扫描wordlist
   -e xor      - 启用扫描xor

以下扫描默认启用;禁用使用-x命令：
   -x accts    - 禁用扫描程序
   -x aes      - 禁用扫描aes
   -x base64   - 禁用扫描base64
   -x elf      - 禁用扫描elf
   -x mail     - 禁用扫描邮件
   -x exif     - 禁用扫描exif
   -x find     - 禁用扫描发现
   -x gps      - 禁用扫描gps
   -x gzip     - 禁用扫描gzip
   -x hiberfile- 禁用扫描hiberfile
   -x httplogs - 禁用扫描httplogs
   -x json     - 禁用扫描json
   -x kml      - 禁用扫描kml
   -x msxml    - 禁用扫描msxml
   -x net      - 禁用扫描net
   -x pdf      - 禁用扫描pdf
   -x rar      - 禁用扫描rar
   -x sqlite   - 禁用扫描sqlite
   -x vcard    - 禁用扫描vcard
   -x windirs  - 禁用扫描windirs
   -x winlnk   - 禁用扫描winlnk
   -x winpe    - 禁用扫描winpe
   -x zip      - 禁用扫描zip
   -x winprefetch - 禁用扫描winprefetch
```

0x02 示例
---------
分析映像文件后，将结果导出到输出目录（-o bulk-out）（xp-laptop-2005-07-04-1430.img）：
```plain
root@kali:~# bulk_extractor -o bulk-out xp-laptop-2005-07-04-1430.img
bulk_extractor version 1.6.0-dev
Hostname: kali
Input file: xp-laptop-2005-07-04-1430.img
Output directory: bulk-out
Disk Size: 536715264
Threads: 1
Phase 1.
13:02:46 Offset 0MB (0.00%) Done in n/a at 13:02:45
13:03:39 Offset 67MB (12.50%) Done in  0:06:14 at 13:09:53
13:04:43 Offset 134MB (25.01%) Done in  0:05:50 at 13:10:33
13:04:55 Offset 201MB (37.51%) Done in  0:03:36 at 13:08:31
13:06:01 Offset 268MB (50.01%) Done in  0:03:15 at 13:09:16
13:06:48 Offset 335MB (62.52%) Done in  0:02:25 at 13:09:13
13:07:04 Offset 402MB (75.02%) Done in  0:01:25 at 13:08:29
13:07:20 Offset 469MB (87.53%) Done in  0:00:39 at 13:07:59
All Data is Read; waiting for threads to finish...
Time elapsed waiting for 1 thread to finish:
     (please wait for another 60 min .)
Time elapsed waiting for 1 thread to finish:
    6 sec (please wait for another 59 min 54 sec.)
Thread 0: Processing 520093696

Time elapsed waiting for 1 thread to finish:
    12 sec (please wait for another 59 min 48 sec.)
Thread 0: Processing 520093696

Time elapsed waiting for 1 thread to finish:
    18 sec (please wait for another 59 min 42 sec.)
Thread 0: Processing 520093696

Time elapsed waiting for 1 thread to finish:
    24 sec (please wait for another 59 min 36 sec.)
Thread 0: Processing 520093696

Time elapsed waiting for 1 thread to finish:
    30 sec (please wait for another 59 min 30 sec.)
Thread 0: Processing 520093696

All Threads Finished!
Producer time spent waiting: 335.984 sec.
Average consumer time spent waiting: 0.143353 sec.
*******************************************
** bulk_extractor is probably CPU bound. **
**    Run on a computer with more cores  **
**      to get better performance.       **
*******************************************
Phase 2. Shutting down scanners
Phase 3. Creating Histograms
   ccn histogram...   ccn_track2 histogram...   domain histogram...
   email histogram...   ether histogram...   find histogram...
   ip histogram...   tcp histogram...   telephone histogram...
   url histogram...   url microsoft-live...   url services...
   url facebook-address...   url facebook-id...   url searches...

Elapsed time: 378.5 sec.
Overall performance: 1.418 MBytes/sec.
Total email features found: 899
```

  [1]: http://digitalcorpora.org/downloads/bulk_extractor/BEUsersManual.pdf
  [2]: https://github.com/simsong/bulk_extractor/
  [3]: http://git.kali.org/gitweb/?p=packages/bulk-extractor.git;a=summary