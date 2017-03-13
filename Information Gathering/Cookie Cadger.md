##Cookie Cadger包描述

Cookie Cadger有助于识别使用不安全HTTP GET请求的应用程序中的信息泄漏。

自2010年Firesheep发布以来，网络提供商已经开始加强合作。如今，大多数主要网站可以在所有事务中提供SSL / TLS，防止Cookie数据通过有线以太网或不安全的Wi-Fi泄漏。但事实是，Firesheep更多的是一个玩具，而不是一个工具。Cookie Cadger是第一个用于拦截和重放特定的不安全的HTTP GET请求到浏览器中的开源笔测试工具。

Cookie Cadgers请求枚举能力

Cookie Cadger是一个图形实用程序，它利用Wireshark套件和Java的强大功能，提供一个完全跨平台，完全开源的实用程序，可以监视有线以太网，不安全的Wi-Fi或加载数据包捕获文件进行离线分析。

**资料来源**：https://www.cookiecadger.com/

[Cookie Cadger首页](https://www.cookiecadger.com/) | [Cookie Cadger报告](http://git.kali.org/gitweb/?p=packages/cookie-cadger.git;a=summary)

- 作者：Matthew Sullivan

- 许可证：FreeBSD

##cookie-cadger包中包含的工具

###cookie-cadger - 有线和无线网络的Cookie审核工具

```
root @ kali：〜＃cookie-cadger --help 
Cookie Cadger，version 1.06 
示例用法：
java -jar CookieCadger.jar 
    --tshark = / usr / sbin / tshark 
    --headless = on 
    --interfacenum = headless = on）-- 
    detection = on 
    --demo = on 
    --update = on 
    --dbengine = mysql（对于基于文件的本地存储，默认为sqlite）-- 
    dbhost = localhost（requires --dbengine = mysql ）-- 
    dbuser = user（requires --dbengine = mysql）-- 
    dbpass = pass（requires --dbengine = mysql）-- 
    dbname = cadgerdata（requires --dbengine = mysql）-- 
    dbrefreshrate = 15 --dbengine = mysql，requires --headless = off） 
    ```
    
   ##Cookie Cadger用法示例
   
   ```
   root @ kali：〜＃cookie-cadger
   ```
