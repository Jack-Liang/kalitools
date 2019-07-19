---
title: dex2jar
categories: Hardware Hacking
tags: [dex2jar,Hardware Hacking,kali linux]
date: 2019-06-25 11:19:00
---
0x00 dex2jar介绍
-------------
dex2jar包含以下这些组件:

- dex读取器，用来读取Dalvik可执行文件(.dex/.odex)。它有与ASM相似的轻量级API。
- dex翻译器，用来进行转换。它以dex-ir格式读入dex指令，经过一些调整，转换为ASM格式。
- dex-ir，在翻译器中使用，用来表示dex指令。
- dex工具，用来处理.class文件。例如：修改apk文件，反混淆jar文件等。
- d2j-smali [待发布]反汇编dex文件，将之还原为smali文件；或从smali文件编译为dex文件。 与smali/baksmali的执行方式不同，两者语法相同，但是本工具支持在desc类型中的转义：“Lcom/dex2jar\t\u1234;”
- dex写入器[待发布]以和dex读取器相同的方式写入数据。

原项目地址: https://github.com/pxb1988/dex2jar/
dex2jar主页 | [Kali上的dex2jar项目](http://git.kali.org/gitweb/?p=packages/dex2jar.git;a=summary)

- 作者: Panxiaobo
- 证书: Apache-2.0

0x01 包含的工具
----------------

##### d2j-jar2dex – 调用dx将jar转换为dex

```
root@kali:~# d2j-jar2dex -h
d2j-jar2dex -- 调用dx将jar转换为dex。
用法: d2j-jar2dex [参数] <目录>
参数:
 -f,--force                   强制覆写
 -h,--help                    显示此帮助信息
 -o,--output <out-dex-file>   输出.dex文件，默认路径是$current_dir/[jar-name]-jar2dex.dex
版本: 0.0.9.15
```

##### d2j-jar-remap–重命名jar文件中的包(package)/类(class)/方法(method)/域(field)

```
root@kali:~# d2j-jar-remap -h
d2j-jar-remap -- 重命名jar文件中的包(package)/类(class)/方法(method)/域(field)
用法: d2j-jar-remap [参数] <jar文件路径>
参数:
 -c,--config <config>    重构用到的的配置文件，此项必须指定
 -f,--force              强制覆写
 -h,--help               显示此帮助信息
 -o,--output <out-jar>   输出.jar文件，默认路径是$current_dir/[jar-name]-remap.jar
版本: 0.0.9.15
在线帮助文档: https://code.google.com/p/dex2jar/wiki/DeObfuscateJarWithDexTool
```

##### d2j-dex2jar–将dex转换为jar

```
root@kali:~# d2j-dex2jar -h
d2j-dex2jar -- 将dex转换为jar
用法: d2j-dex2jar [参数] <0号文件> [其他文件]
options:
 -d,--debug-info              翻译调试信息
 -e,--exception-file <file>   具体的异常信息文件，默认是$current_dir/[file-name]-error.zip
 -f,--force                   强制覆写
 -h,--help                    显示此帮助信息
 -n,--not-handle-exception    不捕获dex2jar抛出的任何异常
 -o,--output <out-jar-file>   输出.jar文件，默认是$current_dir/[file-name]-dex2jar.jar
 -os,--optmize-synchronized   同步调整
 -p,--print-ir                将ir输出到Syste.out
 -r,--reuse-reg               生成java的.class文件时循环使用注册表
 -s                           与--topological-sort/-ts相同
 -ts,--topological-sort       以拓扑逻辑整理块，能够生成更多可读代码
 -v,--verbose                 显示进度
版本: 读取器-1.15, 翻译器-0.0.9.15, ir-1.12
```

##### dex2jar–此工具已被弃用，若可能请使用d2j-dex2jar

```
root@kali:~# dex2jar
此工具已被弃用，若可能请使用d2j-dex2jar。
dex2jar 版本: 翻译器-0.0.9.15
dex2jar file1.dexORapk file2.dexORapk ...
```

##### d2j-jasmin2jar–将.j文件编译为.class文件

```
root@kali:~# d2j-jasmin2jar -h
d2j-jasmin2jar -- d2j-jasmin2jar - 将.j文件编译为.class文件
用法: d2j-jasmin2jar [参数] <路径>
参数:
 -e,--encoding <enc>             指定.j文件编码方式，默认是UTF-8
 -f,--force                      强制覆写
 -g,--autogenerate-linenumbers   自动生成行号
 -h,--help                       显示此帮助信息
 -o,--output <out-jar-file>      输出.jar文件，默认是$current_dir/[jar-name]-jasmin2jar.jar
版本: 0.0.9.15
```

##### d2j-jar-access–增加或移除jar文件中对类(class)/方法(method)/域(field)的访问

```
root@kali:~# d2j-jar-access -h
d2j-jar-access -- 增加或移除jar文件中对类(class)/方法(method)/域(field)的访问
用法: d2j-jar-access [参数] <jar文件>
参数:
 -ac,--add-class-access <ACC>       增加对class中内容的访问
 -af,--add-field-access <ACC>       增加对field中内容的访问
 -am,--add-method-access <ACC>      增加对method中内容的访问
 -f,--force                         强制覆写
 -h,--help                          显示此帮助信息
 -o,--output <out-dir>              指定.j文件输出路径，默认是$current_dir/[jar-name]-access.jar
 -rc,--remove-class-access <ACC>    移除对class中内容的访问
 -rd,--remove-debug                 移除调试信息
 -rf,--remove-field-access <ACC>    移除对field中内容的访问
 -rm,--remove-method-access <ACC>   移除对method中内容的访问
版本: 0.0.9.15
```

##### d2j-asm-verify–校验jar文件中的.class 文件

```
root@kali:~# d2j-asm-verify -h
d2j-asm-verify -- 校验jar文件中的.class 文件
用法: d2j-asm-verify [参数] <0号jar文件> [其他jar文件]
参数:
 -d,--detail   显示详细错误信息
 -h,--help     显示此帮助信息
版本: 0.0.9.15
```

##### d2j-dex-dump

```
root@kali:~# d2j-dex-dump -h
将.dex或.apk文件中的数据dump至out.dump.jar文件中
```

##### d2j-init-deobf–为反混淆jar文件生成初始化配置文件

```
root@kali:~# d2j-init-deobf -h
d2j-init-deobf -- 为反混淆jar文件生成初始化配置文件
用法: d2j-init-deobf [参数] <jar文件>
参数:
 -f,--force                强制覆写
 -h,--help                 显示此帮助信息
 -max,--max-length <MAX>   若长度大于指定的最大值则进行重命名，默认最大值是40
 -min,--min-length <MIN>   若长度小于指定的最小值则进行重命名，默认最小值是2
 -o,--output <out-file>    输出.jar文件，默认是$current_dir/[file-name]-deobf-init.txt
版本: 0.0.9.15
```

##### d2j-apk-sign–用测试证书对apk文件进行数字签名

```
root@kali:~# d2j-apk-sign -h
d2j-apk-sign -- 用测试证书对apk文件进行数字签名。
用法: d2j-apk-sign [参数] <apk文件路径>
参数:
 -f,--force                   强制覆写
 -h,--help                    显示此帮助信息
 -o,--output <out-apk-file>   输出.apk文件，默认路径是$current_dir/[apk-name]-signed.apk
 -w,--sign-whole              对整个apk文件进行签名
版本: 0.0.9.15
```

##### d2j-jar2jasmin–反汇编jar文件中的.class文件至jasmin文件

```
root@kali:~# d2j-jar2jasmin -h
d2j-jar2jasmin -- 反汇编jar文件中的.class文件至jasmin文件
用法: d2j-jar2jasmin [参数] <jar文件路径>
参数:
 -d,--debug              反汇编调试信息
 -e,--encoding <enc>     .j文件的编码方式，默认是UTF-8
 -f,--force              强制覆写
 -h,--help               显示此帮助信息
 -o,--output <out-dir>   .j文件的输出路径，默认是$current_dir/[jar-name]-jar2jasmin/
版本: 0.0.9.15
```

0x02 d2j-dex2jar用法示例
----------------
```
root@kali:~# d2j-dex2jar /usr/share/metasploit-framework/data/android/apk/classes.dex 
dex2jar /usr/share/metasploit-framework/data/android/apk/classes.dex -> classes-dex2jar.jar
```