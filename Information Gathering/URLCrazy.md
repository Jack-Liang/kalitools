# URLCrazy软件包描述

生成和测试域名错误及其变体，以检测域名欺骗、URL劫持、网络钓鱼、企业间谍等活动。

特点

- 能生成15种类型的域名变体
- 已知超过8000个常见的拼写错误
- 支持随机性（宇宙射线引发）的位翻转
- 多种键盘布局（qwerty、azerty、qwertz、dvorak）
- 域名变体有效性检查
- 测试域名变体是否正在使用
- 评估域名变体的流行度

资料来源：http://www.morningstarsecurity.com/research/urlcrazy

[URLCrazy首页](http://www.morningstarsecurity.com/research/urlcrazy) | [Kali URLCrazy资源](http://git.kali.org/gitweb/?p=packages/urlcrazy.git;a=summary)

- 作者：Andrew Horton
- 许可证：Non-commercial

## URLCrazy包含的工具
### urlcrazy - 域名错误生成器
```
root@kali:~# urlcrazy -h
URLCrazy version 0.5
by Andrew Horton (urbanadventurer)
http://www.morningstarsecurity.com/research/urlcrazy

生成和测试域名错误及其变体，以检测域名欺骗、URL劫持、网络钓鱼、企业间谍等活动。

支持以下域名变体：
字符遗漏、字符重复、相邻字符交换、相邻字符替换、双重字符替换、相邻字符插入、缺少点、条形破折号、
单数或复数、常见拼写错误、元音互换、同音词、位翻转（宇宙射线）、同形异义、顶级域名错误和二级域名错误。

用法：/usr/bin/urlcrazy [选项] 域名

选项
 -k，--keyboard=LAYOUT     选项有：qwerty、azerty、qwertz、dvorak（默认：qwerty）
 -p，--popularity          使用Google检查域名流行度
 -r，--no-resolve          不进行域名解析
 -i，--show-invalid        显示无效的域名
 -f，--format=TYPE         Human readable或CSV(默认: human readable)
 -o，--output=FILE         输出文件
 -h，--help                显示帮助信息
 -v，--version             打印版本信息。这个版本是0.5
```
## urlcrazy用法示例

使用dvorak键盘布局（-k dvorak）搜索网址，不对给定域（example.com）解析主机名（-r）：
```
root@kali:~# urlcrazy -k dvorak -r example.com
URLCrazy Domain Report
Domain    : example.com
Keyboard  : dvorak
At        : 2014-05-13 17:04:01 -0600

# Please wait. 95 hostnames to process

Typo Type              Typo            CC-A  Extn
---------------------------------------------------
Character Omission     eample.com      ?     com
Character Omission     examle.com      ?     com
Character Omission     exampe.com      ?     com
Character Omission     exampl.com      ?     com
Character Omission     example.cm      ?     cm
Character Omission     exaple.com      ?     com
```
原文链接：[http://tools.kali.org/information-gathering/urlcrazy](http://tools.kali.org/information-gathering/urlcrazy)
