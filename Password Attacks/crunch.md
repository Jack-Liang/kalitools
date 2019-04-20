# Crunch
************
## Crunch 包描述
************
Crunch是一款词表（字典）生成器，您可以在其中生成指定标准字符集或指定的字符集。Crunch可以产生所有可能的排列和组合。
[crunch 主页](https://sourceforge.net/projects/crunch-wordlist/)
[Kali crunch仓库](https://git.kali.org/gitweb/?p=packages/crunch.git;a=summary)
[资料来源](https：//sourceforge.net/projects/crunch-wordlist//)
作者：bofh28
许可：GPLv2
### 特征
1.crunch以排列组合的方式生成词表（字典）
2.crunch可以按照行数和文件大小来分解输出
3.恢复支持
4.模式支持数字和符号
5.模式现在分别支持大写和小写字符
6.生成多文件时添加状态报告
7.新的-l选项，用于对@,%^的字符支持
8.新的-d选项限制了重复的字符，详细说明请参照man手册
9.Unicode支持
************
### 包含在crunch包中的工具
Crunch-创建一个基于你指定标准的词表（字典）

```
root@kali:~# crunch
crunch 版本 3.6
      
Crunch 可以创建一个基于你指定标准的词表（字典）。  Crunch可以将结果输出到屏幕，文件或者其他程序。
      
用法: crunch <min> <max> [options]
      
其中的min和max是指数字（即字符串的长度范围）
      
      
选项：
-b 指定输出文件大小，只有在有-o START参数存在时才可以使用，输出文件会被分为以开始字符串——截至字符串为名的文件。Eg：./crunch 4 5 -b 20mib -o START 将会生成四个文件：aaaa-gvfed.txt, gvfee-ombqy.txt,ombqz-wcydt.txt, wcydu-zzzzz.txt 有效的类型为kb, mb,  gb,  kib, mib, gib ，前三个类型基于1000，后三个类型基于1024，注意，在数字和类型中间不能有空格，500mb是正确的，而500 mb是错误的。

-c 指定输出文件的行数，只有在有-o START参数存在时才可以使用，输出文件会被分为以开始字符串——截至字符串为名的文件。Eg：./crunch  1  1 -o START -c 60 将会分成两个文件，a-7.txt 和 8-\  .txt，第二个文件的文件名使用\的原因是最后一个字符是 ，而且不得不输出它

-d 限制重复字符的数量。 -d 2@ 限制小写字母输出类似于aab和aac，aaa是不被产生的，因为不会输出三个连续重复的字符

-e 指定停止生成的字符 –e 987 指词表生成到987就停止。

-f/path/to/charset.lst charset-name  从charset.lst中指定字符集，即调用文件

-i 翻转输出结果，如 aaa,aab 你会得到 aaa,baa

-l 当你使用-t参数时，这个参数会告诉crunch 哪个特殊字符（@,%^）需要被视为普通文字，-l参数后跟的字符串长度需要等于 –t参数后跟的字符串长度

-m 和-p参数合并，请使用-p参数替代

-o 指定输出的文件 eg：-o wordlist.txt

-p charset OR -p word1 word2 ... 告诉crunch去生成没有重复字符的词，已排列组合的方式生成词表（字典），其必须为最后一个参数，而且不能和-s一起使用，他忽略了最大最小长度，但是你依然要指定这两个数字

-q filename.txt 告诉crunch去读filename.txt。

-r 告诉crunch从它中断的地方去重新生成词表，-r只在你使用-o参数时才可以使用。你必须使用相同的命令用于继续生成词表。有-s参数时除外，如果你的初始命令时使用了-s参数，那么你一定要移除它在你恢复生成词表之前。只需要在原始命令后加上-r即可

-s 指定开始生成的字符串 eg：-s 03god2fs 即从03god2fs开始生成

-t 指定一个模式 eg：-t @@god@@@@
  @ 会插入小写字母
  , 会插入大写字母
  % 会插入数字
  ^ 会插入特殊符号

-u 该参数禁止打印百分比，他应该为最后一个选项

-z gzip, bzip2, lzma, and 7z   在-o参数后压缩输出，有效参数为gzip, bzip2, lzma,7z。gzip压缩最快但是压缩率是最低的.gzip2比gzip稍慢一点，但是会更好地压缩。7z压缩的最慢，但是他可以最大化压缩率。

请参阅手册页（man）以获取有关如何使用crunch的说明和示例。
```

**********
### Crunch用法示例
使用给定字符（0123456789abcdef）来生成包含最小和最大长度为6的单词的字典文件，将输出保存到6chars.txt
```
root@kali:~# crunch 6 6 0123456789abcdef -o 6chars.txt
Crunch will now generate the following amount of data: 117440512 bytes
（crunch 现在将生成以下数据量：117440512字节）
112 MB
0 GB
0 TB
0 PB
Crunch will now generate the following number of lines: 16777216
（crunch 现在将生成以下函数：16777216）

```

