# Fiked包描述
FakeIKEd简称fiked，是一个假的IKE守护进程。它支持足够的标准和思科扩展，可以以“semi MitM”的方式攻击常见不安全的基于IPsec身份验证设置的Cisco VPN PSK +XAUTH。Fiked可以模拟VPN网关的IKE响应程序，以捕获XAUTH登录凭据; 目前fiked并没有“full MitM”的客户端

**资料来源**:http://www.roe.ch/FakeIKEd

[fiked主页](http://www.roe.ch/FakeIKEd)|[Kali fiked Repo](http://git.kali.org/gitweb/?p=packages/fiked.git;a=summary)

- 作者：Daniel Roethlisberger
- 许可证：GPLv2

## fiked包中包含的工具
### fiked-Cisco VPN攻击工具

```
root@kali：〜＃fiked -h 
用法：fiked [-rdqhV] -g gw -k ID：PSK [-k ..] [-u用户] [-l文件] [-L文件] 
    -r    使用原始套接字：forge ip src addr 匹配<网关>（禁用-u）
    -d    从tty分离并作为守护程序运行（说明-q）
    -q    静默模式，不记录任何东西到stdout 
    -h    显示帮助和退出
    -V    显示版本和退出
    -g gw 模拟网关VPN地址
    -ki：k  预共享密钥，亦称组密码，共享秘密，前缀为其组/密匙ID（第一个-k设置默认值）
    -u 用户 下降到一个非特权用户的权限
    -l 文件 附加结果到凭证日志文件
    -L 文件 verbous 记录为文件而不是stdout
```
## fiked用法示例
```
root@kali:~#即将推出
```
[原文链接](http://tools.kali.org/sniffingspoofing/fiked)
