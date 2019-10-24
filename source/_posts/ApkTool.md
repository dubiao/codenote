---
title: 查看 Apk 文件信息
date: 2019-10-24 11:51:57
categories:
- Android
tags:
- Android
- apk
- apktool
- aapt
---

Apk 信息

## 提取资源 ApkTool
```
$ apktool d my.apk
```

## dex to jar d2j-dex2jar.jar
项目地址：https://github.com/pxb1988/dex2jar
但这个是源码，我是从 [sourceforge](https://sourceforge.net/projects/dex2jar/files/latest/download) 上下载的。
也可以从这里下：[sourceforge](./dex2jar-2.0.zip)
下载解压后，从终端里 cd 到这个目录，然后执行一下：
```
$ chmod +x *.sh
```
这样就可以把所有的`sh`文件变成可执行的了。
（要不然会报错，因为在 d2j-dex2jar.sh 程序里直接执行了 d2j_invoke.sh 程序。但那个程序不能直接执行）
然后就可以通过以后命令来把 dex 文件变成 jar 文件了。
```
$ d2j-dex2jar.sh <classes.dex>
```
这个 `classes.dex` 文件就是把 *apk* 文件当成 *zip* 解压之后里面的那个 *dex* 文件。
如果你的电脑不能直接解压，也可以把 *apk* 文件的后缀名改成 *zip* 就行了。
有些 *apk* 里可能有多个 *dex* 文件。一般大的那个是主要的代码部分，小的有可能是“*加固*”产生的。

## aapt 查看 apk 信息
aapt 一般不在环境变量 PATH 中，一般在
```
$ANDROID_HOME/build-tools/??.?.?/aapt
```
其中的? 代表你用的 build tool 的版本号。各版本间差别不大。

### 查看 apk 中版本、包名、权限、各种语言下的名称和启动的界面（launchable-activity）
```
$ aapt dump badging <myapk.apk>
```
### 其它
可以把*badging* 换成其它参数来输出不同的信息
* strings          Print the contents of the resource table string pool in the APK.
* badging          Print the label and icon for the app declared in APK.
* permissions      Print the permissions from the APK.
* resources        Print the resource table from the APK.
* configurations   Print the configurations in the APK.
* xmltree          Print the compiled xmls in the given assets.
* xmlstrings       Print the strings of the given compiled xml assets.

## 查看 签名信息
### 查看 apk 的签名
1. 用解压软件解压出apk 中 META-INF目录下的CERT.RSA文件
2. 执行  
```
$ keytool -printcert -file path_to/CERT.RSA `
```
会输出 apk 的签名信息，包括 key 的指纹。
也可以用 *jarsigner* 来查看是否已签名。执行
```
$ jarsigner -verify [-verbose] -certs input.apk
```

### 查看 keystore 的信息
执行
```
$ keytool -list -keystore path_to\app_key [-rfc]
```
会输出 key 文件的指纹信息。

加上`-v`参数可以输出更详细的信息：
```
$ keytool -list -v -keystore path_to\app_key [-rfc]
```

执这两条命令要求输入密码。可以在命令后加  -storepass 参数带上密码执行，就不会提示输入了。
```
$ keytool -list -keystore path_to\app_key -storepass pwd
```
