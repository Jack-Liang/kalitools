---
title: Smali
categories: Hardware Hacking
tags: [Smali,Hardware Hacking,kali linux]
date: 2019-06-25 11:23:00
---
0x00  Smali介绍
-------------

smali/baksmali是针对Android的Java虚拟机环境dalvik使用的dex格式的编译/反汇编工具。它的语法大体上基于Jasmin/dedexer 的语法，并支持dex格式的全部功能(注释，调试信息，行信息等等)

源地址: https://github.com/JesusFreke/smali
[smali主页](http://baksmali.com/) | [Kali上的smali软件库](http://git.kali.org/gitweb/?p=packages/smali.git;a=summary)

- 作者: Ben Gruver
- 证书: BSD

0x01 包含的工具
----------------

#### smali–将一组smali文件编译为dex文件

```
root@kali:~# smali --help
用法: smali [-v] [-h] [<命令> [<参数>]]

参数:
  -h,-?,--help - 显示帮助信息
  -v,--version - 显示smali的版本信息并退出

命令:
  assemble(ass,as,a) - 将smali文件编译为dex文件。
  help(h) - 显示帮助信息

使用smali help <命令>来查看特定命令的帮助信息
```

```
root@kali:~# smali help assemble
用法: smali assemble [<参数>] [<文件>|<路径>]+
将smali文件编译为dex文件。

参数:
  -a,--api <api> - 编译时使用的numeric库的api层数。 (默认值是15)
  --allow-odex-opcodes,--allow-odex,--ao - 允许编译同dalvik兼容的odex操作码。
  -h,-?,--help - 显示对应指令的用法说明。
  -j,--jobs <n> - 指定使用的线程数。n是每个核心的线程数。 (默认值是4)
  -o,--output <file> - 指定输出的dex文件名或路径。 (默认文件名是out.dex)
  --verbose - 生成冗余错误信息。
  <[<file>|<dir>]+> - 编译指定的文件。如果指定的是路径，会递归地搜索路径以找到全部的.smali文件。
```

#### baksmali – 对dex文件进行反汇编或dump

```
root@kali:~# baksmali --help
用法: baksmali [--版本] [--帮助] [<指令 [<参数>]]

参数:
  --help,-h,-? - 显示用法说明
  --version,-v - 显示baksmali的版本信息并退出

指令:
  deodex(de,x) - 逆向还原odex/oat文件
  disassemble(dis,d) - 反汇编dex文件。
  dump(du) - 为指定的dex文件输出带注释的16进制dump文件
  help(h) - 显示用法帮助
  list(l) - 列出dex文件中的对象。

使用baksmali help <command>来获取针对特定指令的帮助信息。
```

```
root@kali:~# baksmali help deodex
用法: baksmali deodex [<参数>] <文件>
逆向还原odex/oat文件

参数:
  -a,--api <api> - 被反汇编的文件的numeric库的api层数。 (默认值是-1)
  --accessor-comments,--ac <布朗值> - Generate helper comments for synthetic 
      accessors. 默认开启，使用--accessor-comments=false来禁用(默认值是真)
  --allow-odex-opcodes - 允许反汇编odex操作码，即使输出结果不能被重新编译。
  -b,--bootclasspath,--bcp <类路径> - 一个指定用来在分析dex文件时包含在启动类路径里的文件的列表，每个文件独立成行。如果没有人为指定，baksmali会尝试自动选择合适的默认值。在分析oat文件时，这一路径可以被直接指定为设备的boot.oat文件路径。可以用一个单独的空字串来表示应该使用空启动类路径。(例如 --bootclasspath "")
  使用baksmali help classpath来查看更多帮助信息。
  -c,--classpath,--cp <类路径> - 一个指定用来在分析dex文件时包含在类路径里的额外文件的列表，每个文件独立成行。它们会在执行任何启动类路径指令之后被添加至类路径中。
  --check-package-private-access,--package-private,--checkpp,--pp - 在计算虚表索引时使用包私有访问检查。对于oat文件，这一功能默认开启。对于odex文件，此功能只在处理4.2.0版本的文件时需要开启。在4.2.1版本中已恢复。
  --classes <类> - 指定一个用逗号隔开的类列表。工具将只反汇编这些类。
  --code-offsets,--offsets,--off - 在每一条指令前添加注释，说明它在方法内的代码偏移。
  -d,--classpath-dir,--cpd,--dir <dir> - 指定搜索类路径文件的目录。这条指令可以多次使用以指定多个要搜索的目录。将会以输入这些目录的顺序搜索它们。
  --debug-info,--di <布朗值> - 指定是否在输出中包括调试信息(.local, .param, .line, etc.)。此功能默认开启使用 --debug-info=false来禁用此功能。(默认值是真)
  -h,-?,--help - 显示此指令的帮助信息。
  --implicit-references,--implicit,--ir -为当前文件的方法和字段使用隐式方法和字段引用(不写出类名称)。
  --inline-table,--inline,--it <文件> - 指定一个包含自定义的入列方法表的文件以使用此方法。查看smali Github repo中的"deodexerant"工具以了解怎样从使用dalvik的设备中dump入列方法表。
  -j,--jobs <数值> - 指定使用的线程数。设定对于每一个可用的核心的默认值(默认值为4)
  -l,--use-locals - 在反汇编时，将非参数寄存器的数量输出至.locals而非.registers。
  --normalize-virtual-methods,--norm,--nvm - 在方法已被声明的情况下将virtual方法正常化以使用基类。
  -o,--output <目录> - 指定反汇编文件的输出目录。(默认值是out)
  --parameter-registers,--preg,--pr <布朗值> - 对存放方法参数或是方法入口的寄存器使用pNN语法。此设定默认启用，使用 --parameter-registers=false来禁用它。(默认值是真)
  -r,--register-info <指定的寄存器信息> - 在每一条指令之前或之后增加注释来说明寄存器类型。参数值是用逗号隔开的以下之一：ALL, ALLPRE, ALLPOST, ARGS, DEST, MERGE和FULLMERGE。使用baksmali help register-info来获取更多帮助信息。
  --resolve-resources,--rr <资源前缀> <public.xml文件> - 这条指令将使工具尝试在字节码中搜索全部的资源ID引用，并添加一条含有引用资源的名称的注释。参数可以接受两个值：一个强制的资源前缀和指向public.xml文件的路径。例如：--resolve-resources android.R framework/res/values/public.xml。这项参数可以被多次指定以提供来自多个包的资源。
  --sequential-labels,--seq,--sl - 用符合标记类型的连续序列号来生成标记，而不是使用默认的字节码地址。
  <file> - 指定一个dex/apk/oat/odex文件。对于包含有多个dex文件的apk文件或oat文件，可以直接指定路径，将apk/oat文件当作目录。例如："app.apk/classes2.dex"。
  使用"baksmali help input"来查看更多帮助信息。
```

```
root@kali:~# baksmali help disassemble
用法: baksmali disassemble [<参数>] <文件>
反汇编dex文件。

参数:
  -a,--api <api> - 被反汇编的文件的numeric库的api层数。 (默认值是-1)
  --accessor-comments,--ac <布朗值> - 为人工访问器生成帮助注释。默认是真，使用--accessor-comments=false命令来禁用。(默认值是真)
  --allow-odex-opcodes - 允许反汇编odex操作码，即使反汇编结果可能无法被重新编译
  -b,--bootclasspath,--bcp <类路径> - 一个指定用来在分析dex文件时包含在启动类路径里的文件的列表，每个文件独立成行。如果没有人为指定，baksmali会尝试自动选择合适的默认值。在分析oat文件时，这一路径可以被直接指定为设备的boot.oat文件路径。可以用一个单独的空字串来表示应该使用空启动类路径。(例如 --bootclasspath "")
  使用baksmali help classpath来查看更多帮助信息。
  -c,--classpath,--cp <classpath> - 一个指定用来在分析dex文件时包含在类路径里的额外文件的列表，每个文件独立成行。它们会在执行任何启动类路径指令之后被添加至类路径中。
  --classes <classes> - 指定一个用逗号隔开的类列表。工具将只反汇编这些类。
  --code-offsets,--offsets,--off - 在每一条指令前添加注释，说明它在方法内的代码偏移。
  -d,--classpath-dir,--cpd,--dir <dir> - 指定搜索类路径文件的目录。这条指令可以多次使用以指定多个要搜索的目录。将会以输入这些目录的顺序搜索它们。
  --debug-info,--di <boolean> - 指定是否在输出中包括调试信息(.local, .param, .line, etc.)。此功能默认开启使用 --debug-info=false来禁用此功能。(默认值是真)
  -h,-?,--help - 显示此指令的帮助信息。
  --implicit-references,--implicit,--ir -为当前文件的方法和字段使用隐式方法和字段引用(不写出类名称)。
  --inline-table,--inline,--it <文件> - 指定一个包含自定义的入列方法表的文件以使用此方法。查看smali Github repo中的"deodexerant"工具以了解怎样从使用dalvik的设备中dump入列方法表。
  -j,--jobs <数值> - 指定使用的线程数。设定对于每一个可用的核心的默认值(默认值为4)
  -l,--use-locals - 在反汇编时，将非参数寄存器的数量输出至.locals而非.registers。
  --normalize-virtual-methods,--norm,--nvm - 在方法已被声明的情况下将virtual方法正常化以使用基类。
  -o,--output <目录> - 指定反汇编文件的输出目录。(默认值是out)
  --parameter-registers,--preg,--pr <布朗值> - 对存放方法参数或是方法入口的寄存器使用pNN语法。此设定默认启用，使用 --parameter-registers=false来禁用它。(默认值是真)
  -r,--register-info <指定的寄存器信息> - 在每一条指令之前或之后增加注释来说明寄存器类型。参数值是用逗号隔开的以下之一：ALL, ALLPRE, ALLPOST, ARGS, DEST, MERGE和FULLMERGE。使用baksmali help register-info来获取更多帮助信息。
  --resolve-resources,--rr <资源前缀> <public.xml文件> - 这条指令将使工具尝试在字节码中搜索全部的资源ID引用，并添加一条含有引用资源的名称的注释。参数可以接受两个值：一个强制的资源前缀和指向public.xml文件的路径。例如：--resolve-resources android.R framework/res/values/public.xml。这项参数可以被多次指定以提供来自多个包的资源。
  --sequential-labels,--seq,--sl - 用符合标记类型的连续序列号来生成标记，而不是使用默认的字节码地址。
  <file> - 指定一个dex/apk/oat/odex文件。对于包含有多个dex文件的apk文件或oat文件，可以直接指定路径，将apk/oat文件当作目录。例如："app.apk/classes2.dex"。
  使用"baksmali help input"来查看更多帮助信息。
```

```
root@kali:~# baksmali help dump
用法: baksmali dump [<参数>] <文件>
显示指定的dex文件的带注释的十六进制dump文件

参数:
  -a,--api <api> - 被反汇编的文件的numeric库的api层数。 (默认值是-1)
  -h,-?,--help - 显示此指令的帮助信息。
  <file> - 指定一个dex/apk/oat/odex文件。对于包含有多个dex文件的apk文件或oat文件，可以直接指定路径，将apk/oat文件当作目录。例如："app.apk/classes2.dex"。
  使用"baksmali help input"来查看更多帮助信息。
```

```
root@kali:~# baksmali help list
用法: baksmali list [<参数>] [<指令 [<指令参数>]]
输出dex文件里的的对象。

参数:
  -h,-?,--help - 显示此指令的帮助信息。

指令:
  classes(class,c) - 输出dex文件里的类。
  dependencies(deps,dep) - 输出oedx/oat文件中已存储的依赖。
  dex(d) - 显示apk/oat文件中的dex文件。
  fieldoffsets(fieldoffset,fo) - 显示dex文件中的类的实例字段偏移。
  fields(field,f) - 显示dex文件的字段表中的字段。
  help(h) - 显示此指令的帮助信息。
  methods(method,m) - 显示dex文件的方法表中的方法。
  strings(string,str,s) - 显示dex文件的字串表中的字串。
  types(type,t) - 显示dex文件的类表中的类ID。
  vtables(vtable,v) - 显示dex文件中的虚方法表。
```

0x02 用法示例
----------------

`root@kali:~# 即将推出`