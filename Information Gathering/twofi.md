# twofi软件包描述

当尝试破解密码时，自定义单词列表对于标准字典是非常有用的补充。 最初在“7 Habits of Highly Effective Hackers”博客上发布的一个有趣想法是，使用Twitter来搜索与正在破解的列表相关的关键字，以帮助生成这些自定义单词列表。 这个想法扩展进了twofi，它采用多个搜索关键字来返回单词列表，并按最常见的在前进行排序。

资料来源：http://www.digininja.org/projects/twofi.php

[twofi主页](http://www.digininja.org/projects/twofi.php) | [Kali twofi资源](http://git.kali.org/gitweb/?p=packages/twofi.git;a=summary)

- 作者：Robin Wood
- 许可：Creative Commons Attribution-Share Alike 2.0

## twofi包含的工具
twofi - Twitter单词利用
```
root@kali:~# twofi -h
twofi 1.0 Robin Wood (robin@digininja.org) (www.digininja.org)
twofi - Twitter Words Of Interest

用法：twofi [选项]
--help，-h：            显示帮助
--count，-c：           包含单词计数
--min_word_length，-m： 最小单词长度
--term_file，-T file：  包含关键字列表的文件
--terms，-t：           逗号分隔的搜索关键字。包含空格的要加引号，逗号后面不留空格
--user_file，-U file：  包含用户列表的文件
--users，-u：           逗号分隔的用户名。包含空格的要加引号，逗号后面不留空格
--verbose，-v：         显示详细信息
```

原文链接：http://tools.kali.org/information-gathering/twofi(http://tools.kali.org/information-gathering/twofi)
