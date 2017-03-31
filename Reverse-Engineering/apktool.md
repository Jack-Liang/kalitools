# apktool包描述
apktool用于对第三方的、已编译的Android应用程序(apk文件)进行逆向工程。通过使用该工具，你可以对apk文件进行反编译和解包，所反编译出的文件和编译前几乎一直，另外，也可以修改部分代码并进行重新打包;当然，通过apktool的反编译功能，可以生成支持单步调试的samli工程。同时，由于apktool简化和集成了很多自动化操作，并且采用了统一的工程文件结构，这使得对Android apk文件逆向过程变得很轻松。

apktool绝不是为了满足盗版和其他的非法之需，而是，可以像某个应用的开发者一样，通过使用它对应用完成一些如添加功能、平台适配等本地化的工作，来满足自己的需要。

主要功能：
	
* 对资源文件进行高还原度解码(包括resources.arsc、XMLs和.9.png文件)
* smali 调试：SmaliDebugging
* 高自动化功能
	
**资料来源**:https://code.google.com/p/android-apktool

[apktool Homepage](http://code.google.com/p/android-apktool/)|[Kali apktool Repo](http://git.kali.org/gitweb/?p=packages/apktool.git;a=summary)

- 作者：Brut.alll
- 许可证：Apache-2.0

## apktool包中包含的工具
### apktool Android apk逆向工具

```
root@kali:~# apktool
Apktool v1.5.2 - a tool for reengineering Android apk files
Copyright 2010 Ryszard Wiśniewski <brut.alll@gmail.com>
with smali v1.4.1, and baksmali v1.4.1
Updated by @iBotPeaches <connor.tumbleson@gmail.com>
Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0)

Usage: apktool [-q|--quiet OR -v|--verbose] COMMAND [...]

COMMANDs are:

    d[ecode] [OPTS] <file.apk> [<dir>]
        Decode <file.apk> to <dir>.

        OPTS:

        -s, --no-src
            Do not decode sources.
            不对dex文件进行反编译
        -r, --no-res
            Do not decode resources.
            不对资源文件进行反编译
        -d, --debug
            Decode in debug mode. Check project page for more info.
            调试模式
        -b, --no-debug-info
            Baksmali -- don't write out debug info (.local, .param, .line, etc.)
            反编译不输出调试信息
        -f, --force
            Force delete destination directory.
            强制覆盖已存在文件目录
        -t <tag>, --frame-tag <tag>
            Try to use framework files tagged by <tag>.
            使用framework文件
        --frame-path <dir>
            Use the specified directory for framework files
            framework文件目录
        --keep-broken-res
            Use if there was an error and some resources were dropped, e.g.:
            "Invalid config flags detected. Dropping resources", but you
            want to decode them anyway, even with errors. You will have to
            fix them manually before building.
            当出现错误或者资源文件缺失的时候使用该参数。如提示"Invalid config flags detected. Dropping resources"，但是你仍然想继续解包。这样的话，在进行打包之前，需要手动修复那些错误的文件才能正常进行打包。
            
    b[uild] [OPTS] [<app_path>] [<out_file>]
        Build an apk from already decoded application located in <app_path>.
        对一个在<app_path>下的已经解包的应用工程进行重打包。
        
        It will automatically detect, whether files was changed and perform
        needed steps only.
        apktool会自动检测文件是否修改。

        If you omit <app_path> then current directory will be used.
        <app_path>的默认值为当前目录。
        
        If you omit <out_file> then <app_path>/dist/<name_of_original.apk>
        will be used.
        <out_file>的默认值为<app_path>/dist/<name_of_original.apk>

        OPTS:

        -f, --force-all
            Skip changes detection and build all files.
            跳过文件变动检查，对所有文件进行重打包。
            
        -d, --debug
            Build in debug mode. Check project page for more info.
            调试模式下进行重打包。
            
        -a, --aapt
            Loads aapt from specified location.
            使用指定的aapt。

    if|install-framework <framework.apk> [<tag>] --frame-path [<location>]
        Install framework file to your system.
        安装framework文件。

For additional info, see: http://code.google.com/p/android-apktool/
For smali/baksmali info, see: http://code.google.com/p/smali/

```
## apktool用法示例
使用调试模式对apk文件(/root/SdkControllerApp.apk)进行解包:
```
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
```