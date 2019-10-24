---
title: 浅谈安卓apk加固原理和实现
categories:
- Android
tags:
- Android
- apk加固
url: https://yq.aliyun.com/articles/675072
---

> from [云栖社区](https://yq.aliyun.com/articles/675072)

## 引言：
在安卓开发中，打包发布是开发的最后一个环节，apk是整个项目的源码和资源的结合体；对于懂点反编译原理的人可以轻松编译出apk的源码资源，并且可以修改资源代码、重新打包编译，轻轻松松变成自己的apk或者修改其中一部分窃取用户信息。
代码被反编译对于apk的开发者和使用者而言十分苦恼。apk加固、防止反编译此时显得尤为重要。虽然有好多给apk加固的第三方，可能并不需要自己做apk加固，但是了解apk加固原理还是很有必要的。本文主要向大家介绍apk加固原理和简单实现。
## 目录：
一、apk常见加固方式
二、apk加固原理
三、apk加固实现
四、apk该方式加固后缺陷

## 一、apk常见加固方式
### （1）代码层级加密--代码混淆
代码混淆是一种常用的加密方式。本质是把工程中原来的有具体含义的类名、变量名、方法名，修改成让人看不懂的名字。常见的代码混淆工具proguard（有兴趣的可以自己看一下该工具：http://t.cn/ELjgHdi ）。该加密方式只是对工程提供了最小的保护，并不是说不能逆向破解；只是说难度增加，需要耐心。
### （2） Dex文件加密
dex是Android工程中的代码资源文件，通过dex可以反编译出java代码。dex的加壳是常见的加密方式。通过对dex文件加密拼接加壳，可以有效的对工程代码进行保护。apk工程在安装成功后，app启动时会有dex解密的过程，然后重新加载解密后的dex文件。
第二种加密方式也就是本文要为大家分享的加密方式。基本原理是在jni层， 使用DexClassLoader动态加载技术完成对加密classex.dex的动态加载，dex文件可以附属在assert或raw目录。
## 二、apk加固原理
### (1) apk文件结构
解压一个apk包，可以看到如下目录结构：
assets：存放工程资源(图片、本地html等)文件的目录
Lib：存放ndk编译出来的so文件（so:C/C++编译出的文件）
META-INF：
该目录下存放的是签名信息，用来保证apk包的完整性和系统的安全性：
CERT.RSA：保存着该应用程序的证书和授权信息
CERT.SF：保存着SHA-1信息资源列表
MANIFEST.MF：清单信息
res：存放资源（布局xml、布局xml引用图片等）文件的目录
AndroidManifest.xml：清单文件，它描述了应用的名字、版本、权限、注册的服务等信息
classes.dex：java源码编译经过编译后生成的dalvik字节码文件，主要在Dalvik虚拟机上运行的主要代码部分
resources.arsc：编译后的二进制资源文件
META-INF文件主要是跟签名有关的文件，保证了apk的完整性和安全性。apk每次重新签名需要删除该文件夹。
需要大家主要关注的是classes.dex文件：因为apk加固主要是对dex文件进行的加密。
### (2) Dex文件结构
![](7bbdc476b9d01dc9d9d49eab594f2aff9a34e01d.jpeg)
dex文件可以理解为由java文件编译生产的，直观表现就是dex文件可以编译出java源码；
dex文件的作用是记录整个工程（通常是一个Android工程）的所有类文件的信息；
dex文件是从class文件演变而来的，class文件存在冗余信息，dex文件则去掉了冗余，并且整合了整个工程的类信息。
![](5ebb67010731b6c04e6d6d082cf69f1fb95009c4.jpeg)
文件头header包含了dex文件的信息，也是大家需要关注的部分。因为下面的操作中会有dex文件的修改操作，而判断是否是正确的dex文件是由header部分决定的。
下面看一下header部分的信息：

Header部分有需要注意的三个字段：checksum字段、signature字段、filesize字段。
checksum字段： checksum是校验码字段，校验dex数据的完整性
signature字段： signature是SHA-1签名字段，dex数据完整性校验
signature字段：保存classes.dex文件总长度
之所以关注这三个字段，是因为后面会有对dex的重新拼接。dex拼接后要修改这三个字段，字段修改正确后才可以保证dex的正确加载。
### (3) Dex文件整体加固原理
![](3001322a2d7e4684e4ad175e104a7b290da74888.jpeg)
上图对象解析：
源apk：需要加密的apk程序，源dex来自于源apk
壳程序：Android工程，提供壳dex，壳dex主要作为工程入口，解密出源dex，映射到源dex等操作
加密程序：java工程，主要是做对源dex加密且和壳dex合并成新dex的操作
### (4) 整个工程加载原理
APP启动——>自定义Application中attachBaseContext()方法——>自定义Application工程onCreate()方法——>源Application
1、自定义Application来自于壳程序的dex，加密合成的新dex前半部分就是壳程序的dex，这部分是没任何问题，可以正常加载。该Application中attachBaseContext方法会做解密操作，解密出源dex并放置在固定目录下，添加dex的加载映射；映射到源dex目录。
2、自定义Application工程onCreate()方法添加源dex加载的入口；即源dex的application和mainActivity。
3、程序正常启动；源dex被正确加载。
## 三、apk加固实现
准备：
SourceProject：
需要加密源程序,自定义application为：
com. targetapk
MyApplication，主activity为：
com. targetapk.MainActivity
jiaguApk：java工程，dex加密合并操作
shellApk：android工程，提供壳dex；自定义Application设定为：
org.hackcode.ProxyApplication
SourceProject是简单的Android工程demo，编译生成生成被壳加密的sourceProject.apk
jiaguApk是主要作用是加密源sourceProject.apk中dex文件；然后拼接到壳dex后面生成新的dex
shellApk是壳工程，主要是作为加密后apk的伪入口，加密后的apk工程会先加载壳工程提供Application：org.hackcode.ProxyApplication，解密、映射等操作
整体加密步骤：
1.反编译目标app(sourceProject.apk)，得到sourceProject文件；sourceProject.apk来源于SourceProject工程
2.修改sourceProject文件中的manifest文件，将自定义Application设定为“org.hackcode.ProxyApplication”
3.拿到sourceProject文件中的dex文件，压缩为TargetApk.zip
4.反编译壳apk：apktool.bat d shellApk.apk，得到shellApk文件
5.拿到shellApk文件下的classes.dex和TargetApk.zip，加密合成新的classes.dex文件
6.新合成的class.dex替换sourceProject文件中的class.dex
7.删除sourceProject文件中的META-INF文件，重压缩成zip文件
8.重新签名
步骤2主要是是为了加载壳dex中的代码；正确解析dex。
步骤6主要是jiaguApk工程的工作。
jiaguApk关键代码
![](94feb86c7a47eee8e2b36f329ca9047cdcd8afd0.jpeg)
以上代码主要作用是源程序dex压缩成TargetApk.zip后加密，加密后拼接在壳dex的后面，然后生成新的dex文件，dex文件修改头部参数，保证dex文件正确读取。
此时生成的新的dex文件前部分是能正确被运行的壳dex的代码。
shellApk壳工程关键代码
![](9e637286c8cc194e47a8546b28cdfb4e58f360aa.jpeg)
attachBaseContext方法：
主要作用是程序apk中dex拷贝、解密出源dex放在data/data目录下；设置dex加载目录映射。
![](7ee35cd597c457a94a775a5033b341e8ccce9222.jpeg)
onCreate：
主要作用替换源应用dex的application，使解密出的源dex正确加载；保证源入口正确，保证项目正确加载。
以上就是apk加壳实现整个过程。实现起来基本没什么问题，需要注意的点是源工程有多dex问题：源程序中有多个dex的时候，多个dex同时一块压缩成TargetApk.zip，然后其他步骤不变。亲测没问题！
## 四、apk该方式加固后缺陷
### （1）首次打开加载慢的问题。
加固后的工程首次打开会有延时，延时时间会跟源工程的dex大小有关。就拿普元客户端来说，里面有两个dex，总共有8M左右；加固后首次打开会慢3s左右；而且以后每次打开会有2s左右的延时。
### （2）安全性问题。
大家会发现源dex文件还是会落地，在工程的data/data目录下面，越狱的手机可以直接看到。拿到dex资源，一样可以通过反编译拿到java代码。网上有不落地的方法，尝试一直没有成功；如果哪位大神有可行方法的话，欢迎分享交流。

原文发布时间为：2018-12-4
本文作者：张存征
本文来自云栖社区合作伙伴“ [EAWorld](https://yq.aliyun.com/go/articleRenderRedirect?url=https%3A%2F%2Fmp.weixin.qq.com%2Fs%2Fw1m9bI0-fFDCxMLkzi8_1g) ”，了解相关信息可以关注“EAWorld”微信公众号
