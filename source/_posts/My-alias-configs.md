---
title: My alias configs
categories:
- dev
- bash
date: 2021-01-14 12:16:24
tags:
- bash
---

日常工作中有很多操作繁琐而常用，尤其是一些命令或代码很长，必要的参数也很多，有时候记不住那么多，或是一个个打出来很费时间。一个比较好的解决办法是就是使用 shell 的 alias 命令来给一些命令加一个“快捷方式”，省下来的时候可以再挣个百八十万了。

### alias命令

> alias: 别名 化名

大部分（几乎所有）的bash环境都提供了`alias`命令。
常用语法如下：
```bash
alias a='ls -l'
```

当你执行完这句命令，之后再在终端里输入`a`再回车，就相当于执行了`ls -l`。如果命令比较短，中间没有空格或其它需要转义的符号，可以不用写引号。不过还是建议在定义alias时，总是加引号。

需要加参数的方式也很简单，不过只支持在后面加。中间无法替换变量。
比如，对于如上已定义的`a`：
```bash
a ~/Downloads/
```
就想当于执行了 ls -l ~/Downloads/

可以看到在执行时，相当于直接用 `ls -l` 替换了 `a` 然后执行。

### alias 分享

如下分享我常用的 alias 定义。

```bash

## 目录相关
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias _='sudo'
alias c='clear'
alias cd..='cd ..'

alias l='ls -a'
alias l1='ls -1'
alias la='ls -AF'
alias ll='ls -al'
alias ls='ls -G'
alias sl='ls'

alias md='mkdir -p'
alias rd='rmdir'

## 其它
alias grep='grep --color=auto'
alias cls='clear'
alias k='clear'
alias h='history'
alias q='exit'

## 网络
alias port='netstat -an | grep ' #商品号占用

##代码
alias py='python'
alias rb='ruby'
### git
alias gitreset='git reset --hard'
alias gitpull='git pull'
alias gitresetpull='git reset --hard && git pull'
alias gitresetcheck='git reset --hard && git checkout' # + 分支名
#恢复文件
alias gitresetfile='git checkout HEAD --' ## 加文件名

## 程序
alias vbpf='vim ~/.bash_profile'
alias vbrc='vim ~/.bashrc'

alias snano='sudo nano'
alias svim='sudo vim'
alias vhosts='sudo vim /etc/hosts'


#adb 命令，系统安装了adb程序，且adb在环境变量中时可用
alias adb8081='adb reverse tcp:8081 tcp:8081'
alias adbback='adbkey KEYCODE_BACK'
alias adbdesk='adb shell am start -n ' # 形如 com.android.launcher3/.Launcher  的包名类名

# 模拟按键
alias adbkey='adb shell input keyevent'
alias adbhome='adbkey KEYCODE_HOME'
alias adbpow='adbkey KEYCODE_POWER'
alias adbtask='adbkey KEYCODE_APP_SWITCH'


alias adbtop='adb shell dumpsys window windows | grep -E '\''mCurrentFocus|mFocusedApp'\'''
alias adbpackage='adb shell pm list packages | grep ' # 加包名的一部分
alias adbkill='adb shell am force-stop ' #包名

# 截图
alias adbshoot='adb exec-out screencap -p > /tmp/adbscreencap.png && open /tmp/adbscreencap.png'

#adb 录屏，仅在已连接设备的shell中可执行 screenrecord 程序时可用
alias adbrecord='adb shell screenrecord  /data/local/tmp/screenrecord.mp4'
alias adbrecord_del='adb shell rm -f /data/local/tmp/screenrecord.mp4'
alias adbrecord_open='adb pull  /data/local/tmp/screenrecord.mp4 /tmp/adbscreenrecord.mp4 && open /tmp/adbscreenrecord.mp4'
alias adbrecord_pull='adb pull /data/local/tmp/screenrecord.mp4 ./'
alias adbrecord_pull_to='adb pull /data/local/tmp/screenrecord.mp4'
alias adbrecord_rate='adb shell screenrecord  /data/local/tmp/screenrecord.mp4 --bit-rate'
alias adbrecord_time='adb shell screenrecord  /data/local/tmp/screenrecord.mp4 --time-limit'

alias adbinstall='find . -name "*.apk" -maxdepth 1 && find . -name "*.apk" -maxdepth 1 -exec echo "adb install -r {}" \; -exec adb install -r {} \;' # 安装此目录下所有的apk


```
