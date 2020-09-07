# DirBuster软件包描述
DirBuster是一个用来在web/应用服务器上爆破目录与文件的多线程Java应用程序。通常情况下，某些web服务器看上去是处于默认设置的状态，然而实际上有一些页面和应用是被隐藏于其中的。DirBuster的作用就是尝试去发现这些隐藏的内容。然而，这种性质的爆破工具经常受制于目录与文件的字典大小。因此，DirBuster提出了一种新的方法来尝试解决这个问题：可以从网上抓取下来的目录与文件信息（其实际上被开发者所使用）从头生成字典！DirBuster自带了整整9个不同的字典文件，使得其在寻找隐藏的目录和文件上有着很棒的效率。如果这样还不能满足你，那么DirBuster还提供了纯爆破（pure brute force）的选项，让那些隐藏的目录和文件无处遁形。

资料来源：https://www.owasp.org/index.php/Category:OWASP_DirBuster_Project

[DirBuster首页](https://www.owasp.org/index.php/Category:OWASP_DirBuster_Project) | [Kali DirBuster仓库](https://gitlab.com/kalilinux/packages/dirbuster)

- 作者：Whitel
- 许可证：商业

## DirBuster包中的工具
### dirbuster - web服务器目录爆破工具
DirBuster应用程序

## DirBuster用法示例
```
root@kali:~# dirbuster
```
![error](http://tools.kali.org/wp-content/uploads/2014/02/dirbuster.png)

