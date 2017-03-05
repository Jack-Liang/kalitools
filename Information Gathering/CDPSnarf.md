#CDPSnarf软件包描述

CDPSnarf是专门用于从CDP包中提取信息的网络嗅探器。
它提供了所有信息“show cdp neighbors detail”命令将在Cisco路由器上返回，甚至更多。

功能列表如下：

- CDP广告之间的时间间隔
- 源MAC地址
- CDP版本
- TTL
- 校验和
- 设备ID
- 软件版本
- 平台
- 地址
- 端口ID
- 能力
- 双工
以PCAP转储文件格式保存数据包
从PCAP转储文件读取数据包
调试信息（使用“-d”标志）
使用IPv4和IPv6测试
资料来源：https://github.com/Zapotek/cdpsnarf 

[CDPSnarf首页](https://github.com/Zapotek/cdpsnarf) | [卡利CDPSnarf回购](http://git.kali.org/gitweb/?p=packages/cdpsnarf.git;a=summary)

- 作者：Tasos“Zapotek”Laskos
- 许可证：GPLv2

##cdpsnarf包中包含的工具

###cdpsnarf - 提取CDP信息的网络嗅探器

```
root @ kali：〜＃cdpsnarf -h 
CDPSnarf v0.1.6 [$ Rev：797 $]发起。
   作者：Tasos“Zapotek”Laskos 
           <tasos.laskos@gmail.com> 
              <zapotek@segfault.gr> 
   网站：http://github.com/Zapotek/cdpsnarf 

cdpsnarf -i <dev> [-h] [-w savefile ] [-r dumpfile] [-d] 

   -i定义嗅探的接口
   -w将数据包写入PCAP转储文件
   -r从PCAP转储文件读取数据包
   -d显示调试信息
   -h显示帮助消息并退出
   ```
  ##cdpsnarf用法示例

###在接口**eth0（-i）**上嗅探，并将捕获写入名为**cdpsnarf.pcap（-w）**的文件：
