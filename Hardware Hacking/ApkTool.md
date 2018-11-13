### # apktool #


### apktool 工具包描述 ###
 
   这是一款用于逆向工程、回编译、逆向二进制app的工具。它可以解码资源到几乎最初开发时的形式，并可以在修改之后重新构建它们;它提供了断点调试功能而且使得重新构建工程文件结构自动化,简单化，省去了大量重复工作，例如：打包apk文件等。 


### 特点: ###

 
 * 解码资源到最初的状态(其中包括.arsc，xmls和9.png等资源文件)并复原他们到开发时的状态。
 * smali (可以理解为android的汇编码)调试功能。
 * 提高逆向效率，减少重复工作。


源码：: [https://code.google.com/p/android-apktool/]( https://code.google.com/p/android-apktool/)

[apktool 主页](https://code.google.com/p/android-apktool/) | [Kali apktool 仓库](http://git.kali.org/gitweb/?p=packages/apktool.git;a=summary)


 * 作者：Brut.alll
 * 协议：Apache-2.0


### apktool工具介绍 ###


	
	Apktool v1.5.2 - 一款用于逆向安卓文件的工具
	版权归于 2010 Ryszard Wiśniewski <brut.alll@gmail.com>
	包括 smali v1.4.1, 和 baksmali v1.4.1
	更新 @iBotPeaches <connor.tumbleson@gmail.com>
	Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0)
	
	语法: apktool [-q|--quiet OR -v|--verbose] COMMAND [...]
	
	命令:

    d[编码] [选项] <file.apk> [<路径>]    解码 <file.apk> 到 <路径>.

        选项:

        -s, --no-src
          	不解码源代码文件
        -r, --no-res
            不解码资源文件
        -d, --debug
            开启debug解码模式，查看项目页查看更多信息
        -b, --no-debug-info
            拷贝模式 -- 不写入debug语句 (.local, .param, .line, etc.)
        -f, --force
            强制删除目标文档
        -t <tag>, --frame-tag <tag>
          使用framwork层系统资源标签模式
        --frame-path <dir>
          使用特定目录存放framwork层系统资源
        --keep-broken-res
         	当某些需要被反编的资源存在错误，例如：无效的标签对，但是你仍然想要反编他们即使他们存在错误，那你首先要在编译构建它们之前手动修复它们。

   	语法:  b[uild] [OPTS] [<app_path>] [<out_file>]

		编译打包apk，指定某个路径中被反编译的程序文件
 
		工具将自动检测文件的改变以及组织形式通过几个步骤

        If you omit <app_path> then current directory will be used.
		省略路径参数，默认为当前目录
        If you omit <out_file> then <app_path>/dist/<name_of_original.apk>
        will be used.
		假如省略输出文件名称，那么app原来的路径dist目录下生成重新回编译打包的apk文件以原文件命名

        OPTS:

        -f, --force-all
           跳过检测直接编译打包
        -d, --debug
           debug编译模式
        -a, --aapt
            加载aapt工具从自定义的目录下

    if|install-framework <framework.apk> [<tag>] --frame-path [<location>]
        Install framework file to your system.
	假如选择了设置framework层资源标签，首先需要指定该apk安装的路径

	更多查看: http://code.google.com/p/android-apktool/
	更多查看: smali/baksmali info, see: http://code.google.com/p/smali/		


### apktool 使用实例 ###

#### 使用debug模式反编译 /root/SdkControllerApp.apk文件 ####

	
	root@kali:~# apktool d /root/SdkControllerApp.apk
	I: Baksmaling...
	I: Loading resource table...
	I: Loaded.
	I: Decoding AndroidManifest.xml with resources...
	I: Loading resource table from file: /root/apktool/framework/1.apk
	I: Loaded.
	I: Regular manifest package...
	I: Decoding file-resources...
	I: Decoding values */* XMLs...
	I: Done.
	I: Copying assets and libs...




**译者：SunnyAndroid**

 **校对：-**


> 译者的话：
>  现在一般使用android killer 集成好的一键反编译工具，反编译jar工具包最好使用shakalaka，通过动态和静态方式(idea wireshake)结合抓包工具调试破解手机软件。