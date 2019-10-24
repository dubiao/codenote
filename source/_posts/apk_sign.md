---
title: APK 签名
date: 2019-10-24 13:44:33
categories:
- Android
tags:
- Android
- apk
- apksigner
- 签名
---
## APK 签名
### 签名v1 v2
从Android 7.0开始, 谷歌增加新签名方案 V2 Scheme (APK Signature);
但Android 7.0以下版本, 只能用旧签名方案 V1 scheme (JAR signing)

#### V1签名:
    来自JDK(jarsigner), 对zip压缩包的每个文件进行验证, 签名后还能对压缩包修改(移动/重新压缩文件)
    对V1签名的apk/jar解压,在META-INF存放签名文件(MANIFEST.MF, CERT.SF, CERT.RSA),
    其中MANIFEST.MF文件保存所有文件的SHA1指纹(除了META-INF文件), 由此可知: V1签名是对压缩包中单个文件签名验证

#### V2签名:
    来自Google(apksigner), 对zip压缩包的整个文件验证, 签名后不能修改压缩包(包括zipalign),
    对V2签名的apk解压,没有发现签名文件,重新压缩后V2签名就失效, 由此可知: V2签名是对整个APK签名验证

#### V2签名优点:
       * 签名更安全(不能修改压缩包)
       * 签名验证时间更短(不需要解压验证),因而安装速度加快

注意: apksigner工具默认同时使用V1和V2签名,以兼容Android 7.0以下版本

### 签名原理
对一个APK文件签名之后，APK文件根目录下会增加META-INF目录，该目录下增加三个文件：
```
MANIFEST.MF
NETEASE.RSA
NETEASE.SF
```

其中 *.RSA* 文件还可能是 *.DSA* 文件，RSA与SF文件的文件名可以更改，但是它们的命名必须一样。
*MANIFEST.MF* 中保存了APK里所有文件的SHA1校验值的BASE64编码，格式如下（一个文件对应一条记录）：
```
Name: res/anim/abc_fade_in.xml
SHA1-Digest: ohPEA4mboaFUu9LZMUwk7FmjbPI=
Name: res/anim/abc_fade_out.xml
SHA1-Digest: MTJWZc22b5LNeBboqBhxcQh5xHQ=
```
*.SF* 文件里保存了 *MANIFEST.MF* 文件的SHA1校验值的BASE64编码，同时还保存了MANIFEST.MF中每一条记录的SHA1检验值BASE64编码，格式如下：
```
SHA1-Digest-Manifest: ZRhh1HuaoEKMn6o21W1as0sMlaU=
Name: res/anim/abc_fade_in.xml
SHA1-Digest: wE1QEZhFkLBWMw4TRtxPdsiMRtA=
Name: res/anim/abc_fade_out.xml
SHA1-Digest: MfCV1efdxSKtesRMF81I08Zyvvo=
```
*.RSA* 文件则包含了签名的公钥、签名所有者等信息，还保存了用SHA1withRSA签名算法对SF文件的签名结果信息。

Android系统就是根据这三个文件的内容对APK文件进行签名检验的。

## 签名
有多种签名方式。通常应该在签名前进行 *ZipAlign* 的操作（字节对齐），可以使得 app 更快的被加载和执行。
### apksigner
apksigner 一般不在环境变量 PATH 中，一般在
```
$ANDROID_HOME/build-tools/??.?.?/apksigner
```
其中的? 代表你用的 build tool 的版本号。各版本间差别不大。

```
USAGE: apksigner <command> [options]
       apksigner --version
       apksigner --help

EXAMPLE:
       apksigner sign --ks release.jks app.apk
       apksigner verify --verbose app.apk

apksigner is a tool for signing Android APK files and for checking whether
signatures of APK files will verify on Android devices.
COMMANDS
sign          Sign the provided APK
verify        Check whether the provided APK is expected to verify on Android
version       Show this tool's version number and exit
help          Show this usage page and exit
```

默认情况下，签名后会替换原来的apk 文件（inplace）可以指定 `--in` 和 `--out` 参数来防止源文件被替换
```
$ apksigner sign --ks release.jks --in app.apk --out app-signed.apk
```

### jarsigner

```
jarsigner -verbose -keystore <path_to/key> -signedjar signed.apk unsigned.apk  -keypass <thekeypass> -storepass <thestorepass> <thealias>
```

> jarsigner在对一个已经有META-INF目录的APK进行签名的时候，有可能会报错：
> ```
> jarsigner: 无法对 jar 进行签名: java.util.zip.ZipException: invalid entry compressed size (expected ? but got ? bytes)
> ```

-我没用过哈，不知道情况。-

## ZipAlign
zipalign 一般不在环境变量 PATH 中，一般在
```
$ANDROID_HOME/build-tools/??.?.?/apksign
```
其中的? 代表你用的 build tool 的版本号。各版本间差别不大。

使用以下命令来对齐字节：
```
zipalign [-p] [-v] 4 infile.zip outfile.zip
```

可以查看当前 apk 是否已对齐
```
zipalign -c [-p] [-v] 4 infile.zip
```

一般 zipalign 在签名之前进行。可以在v1版本的签名之后进行，但必需要在 v2 的签名之前进行。因为 v2 的签名是对整个包文件的签名，任何对包的修改都会导致签名失效。

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

### 查看 key 的信息
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
