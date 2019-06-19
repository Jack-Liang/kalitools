# MFOC [Mifare Classic Offline Cracker]
## 项目主页
> https://github.com/nfc-tools/mfoc.git

## 简介
MFOC是一款用于实施Nethemba"离线嵌套"攻击的开源软件。

此程序允许从MIFARE Classic卡中恢复身份验证密钥。

请注意，MFOC只有在具有已知密匙时才能从目标恢复其他密钥: 默认密钥(在MFOC中使用硬编码) 或自定义密钥(由用户通过命令行输入)。


## 从源码编译
```
$ git clone https://github.com/nfc-tools/mfoc.git
$ cd mfoc
$ autoreconf -is
$ ./configure
$ make && sudo make install
```

## 用法
```
root@kali:~# mfoc -h
Usage: mfoc [-h] [-k 密钥] [-f 密钥文件] ... [-P 探测值] [-T 容差值] [-O 输出文件]

  h     打印帮助信息并退出
  k     尝试默认密钥和指定密钥
  f     解析除默认密钥之外还要添加的密钥文件
  P     每个扇区的探测值，默认值20
  T     指定每次使用随机数的容差范围，默认值20
        (即，总容差范围为40，上下浮动范围为20)
  O     导出卡中数据到指定文件(必选)
  D     如果没有PRNG漏洞，导出卡的部分数据到指定文件

示例: mfoc -O mycard.mfd
示例: mfoc -k ffffeeeedddd -O mycard.mfd
示例: mfoc -f keys.txt -O mycard.mfd
示例: mfoc -P 50 -T 30 -O mycard.mfd

此mfoc版本为 0.10.7
更多帮助信息请运行 'man mfoc'
```


