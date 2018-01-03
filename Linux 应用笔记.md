---
title: Linux 应用笔记
tags: Linux,应用笔记,小书匠, Raspberry Pi 
grammar_footnote: true
grammar_cjkEmphasis: true
grammar_cjkRuby: true
---

[TOC]

# 常用命令
**linux是32位还是64位**
`getconf LONG_BIT`

**Linux 如何查看用户id**
cat /etc/passwd | grep <你的用户名>来查看你的ID。 

 vcgencmd measure_clock < clock >
vcgencmd measure_temp

**如何按最后修改时间对 ls 命令的输出进行排序**
ls -lt

**修改时区**
（将Asia/shanghai-上海时区写入当前时区）`#cp -f /usr/share/zoneinfo/Asia/Shanghai     /etc/localtime`

查看时区 `date -R` 

**实时查看LOG**
 `tail -f /var/log/messages`

**查看端口占用情况的命令**
```
lsof -i
lsof -i:21
netstat -apn|grep <端口号>
ps -aux|grep <进程号>
```

**Ubuntu 查看文件以及磁盘空间大小管理**
```
查看当前文件夹下所有文件大小（包括子文件夹）
du -sh

查看指定文件夹下所有文件大小
du -h ftp
 
查看指定文件夹大小
# du -hs ftp
6.3G    ftp

参数查看磁盘剩余空间信息
df -hl

下面是相关命令的解释：
df -hl 查看磁盘剩余空间
df -h 查看每个根路径的分区大小
du -sh [目录名] 返回该目录的大小
du -sm [文件夹] 返回该文件夹总M数
```

**删除用户和主目录**
`userdel -rf eric`



# CentOs
**安装**
[CentOS下载][1] 
> Centos 中文站

[CentOS 7.0系统安装配置图解教程][2]
> 使用UltralISO 制作U盘镜像

[CentOS7.2更改yum源与更新系统][3]
`wget http://mirrors.163.com/.help/CentOS7-Base-163.repo`


**Samba的安装与配置**
 [CentOS7下Samba的安装与配置][4]
[Samba Server Installation and Configuration on CentOS 7][5]
>这里主要注意的点是  firewall的端口开启   另外  目前我们还没有尝试带 账号密码的登录

[centos下yum安装samba及配置][6]
[CentOS 7安装配置Samba服务器][7]

**安装GitBlit服务**
[CentOS上安装GitBlit服务][8]

**FTP**
[CentOS7 添加FTP用户并设置权限][9]
[centos 7开启FTP以及添加用户配置权限，只允许访问自身目录，不能跳转根目录][10]

# Raspberry
**[raspberrypi 官网][11]**
账号 zozo
邮箱 52964447@qq.com
密码 engineer

**[树莓派论坛][12]**

账号 zozo825117
密码 engineer
邮箱 52964447@qq.com

[树莓派开发系列教程2——树莓派上手使用][13]

[树莓派 40Pin 引脚对照表][14]
**串口访问**
[通过串口连接树莓派ssh][15]
![enter description here][17]

**更换阿里云更新源方法**
[树莓派换源（用的是阿里的源）亲测！！][18]
>原sources.list文件中第一行deb http://mirrordirector.raspbian.org/raspbian/ jessie main contrib non-free rpi，明确告诉你是jessie的，基于deb 8了，但是楼主给的确是wheezy版本，基于deb 7版本的，会出很多错误的，现在最新的jessie 阿里云上还没有啊
可以使用Raspberry Pi Raspbian 系统 Debian 8（jessie）使用清华大学源
`deb http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ jessie main non-free contrib
deb-src http://mirrors.tuna.tsinghua.edu.cn/raspbian/raspbian/ jessie main non-free contrib`




**[树莓派键盘布局设置][19]**

**挂载硬盘**
[linux使用ntfs-3g 挂载NTFS分区][20]
[给树莓派挂载移动硬盘或U盘][21]

**远程**
[【树莓派】树莓派上面安装配置teamviewer][22]

**服务器**
[【合集】用Raspberry Pi（树莓派）打造各种服务器][23]

**samba**
[\[教程\] 树莓派搭建NAS服务器][24]

[我的树莓派3B — Raspberry Pi 树莓派 开发板 开箱_开箱晒物_什么值得买][25] 

**代理服务**
[linux命令行模式下实现代理上网 - 成长全记录 - 51CTO技术博客][26] 
[修改树莓派更新源及设置代理配置][27]
[Unable to Install using apt-get][28]


[Kodi Pi wiki][29]

[树莓派3+安装centos][30]
[树莓派的启动流程][31]


**audio**
[在树莓派上播放音频][32]
[USB mic on Linux][33]
[ALSA音频工具amixer,aplay,arecord][34]
[PLAYING AUDIO ON THE RASPBERRY PI][35]

**avs**
[alexa/alexa-avs-sample-app][36]
[打造DIY版Echo：树莓派+ Alexa 语音服务][37]
[Exception in thread "Thread 24" !][38]
>`mvn install -Dalpn-boot.version=8.1.6.v20151105 `
`mvn exec:exec -Dalpn-boot.version=8.1.6.v20151105`

[Build fails, needs jack added to dependency libs #418][39]
>We have an internal ticket filed to work on supporting stretch in a future release. In the mean time, it should work with Jessie.

[Amazon AVS - Conexant][40]
>官方套件
>
[Conexant2Mic Raspberry Pi][41]

# Ubuntu
[Ubuntu 16.04 LTS安装 TeamViewer 远程协助软件][42]

[Ubuntu下ssh服务的安装与登陆（ssh远程登陆）][43]




# 实用教程
## Vim
[Vim入门基础][44]

[Debian下安装vim][45]

[vim配色方案设置（更换vim配色方案）][46]


## 权限问题
**Username is not in the sudoers file. This incident will be reported**

To solve this I followed below steps:
* go to home directory by running command "cd -"
* then type 'su -'it will ask you for password then type your login password you will be in root user.
 ```
 [shri@localhost ~]$ su - 
 Password: 
 [root@localhost ~]# vi /etc/sudoers 
 ```
* then add
`username        ALL=(ALL)      ALL`
to sudoers
* save and exit

**Vim edit the read-only file**
try to save using ‘:w!’, SHIFT+ZZ, or :qw!, 

## 内存分配
**[安装Ubuntu时如何手动指定分区（高级分区）][47]**

**[Linux挂载点介绍及桌面服务器分区方案][48]**

**boot 空间不够的问题**
[清理CentOS的/boot分区][49]
[How to solve low disk space on /boot/ in CentOS 7][50]


## shell 脚本
**[shell 之空格][51]**

[Shell脚本实现自动修改IP地址][52]


**[Linux---CentOS 定时执行脚本配置][53]**
> 使用root账号 解决shell权限问题  shell里面用的都是绝对路径

[crontable  命令 详解][54] 

**[教你如何比谷歌搜索更快速有效地利用 man][55]**

**[Python实现树莓派WiFi断线自动重连的实例代码][56]**



# 收藏备份
## 收藏
**[Linux中国][57]**
![enter description here][58]

**[鸟哥的 Linux 私房菜 -- 基础学习篇目录][59]**

## 备份

## 调试笔记
### 1708


  [1]: http://www.centoscn.com/CentosSoft/
  [2]: http://www.osyunwei.com/archives/7829.html
  [3]: http://blog.csdn.net/weixin_35934768/article/details/52637273
  [4]: http://wangzhijian.blog.51cto.com/6427016/1698879
  [5]: https://www.howtoforge.com/samba-server-installation-and-configuration-on-centos-7
  [6]: http://www.centoscn.com/CentosServer/ftp/2015/0907/6138.html
  [7]: http://www.centoscn.com/CentosServer/ftp/2015/0622/5707.html
  [8]: http://www.cnblogs.com/sanghg/p/5655880.html
  [9]: http://blog.csdn.net/mayday920723/article/details/53173263
  [10]: http://blog.csdn.net/qq_32835907/article/details/73201403
  [11]: https://www.raspberrypi.org/
  [12]: http://bbs.shumeipaiba.com/forum.php
  [13]: http://blog.csdn.net/xdw1985829/article/details/38779827
  [14]: http://shumeipai.nxez.com/raspberry-pi-pins-version-40
  [15]: http://blog.csdn.net/talkxin/article/details/50493414
  [16]: ./images/1503026529375.jpg
  [17]: ./images/1503026529375.jpg 
  [18]: http://blog.csdn.net/guyang1995/article/details/53908080
  [19]: https://wenku.baidu.com/view/f0838b0d6bec0975f565e25f.html
  [20]: http://jingyan.baidu.com/article/b7001fe17978900e7282ddd1.html
  [21]: http://shumeipai.nxez.com/2013/09/08/raspberry-pi-to-mount-the-removable-hard-disk.html
  [22]: http://www.cnblogs.com/haochuang/p/6743800.html
  [23]: http://blog.csdn.net/xzknet/article/details/38989471
  [24]: http://www.eeboard.com/bbs/thread-27434-1-1.html
  [25]: https://post.smzdm.com/p/514045/
  [26]: http://lymrg.blog.51cto.com/1551327/425744
  [27]: http://blog.csdn.net/mouse1598189/article/details/53616394
  [28]: https://www.raspberrypi.org/forums/viewtopic.php?f=63&t=17016
  [29]: http://kodi.wiki/view/Raspberry_Pi
  [30]: http://blog.csdn.net/meteorite91/article/details/71157145
  [31]: https://www.hitoy.org/raspberry-pi-boot-process.html
  [32]: http://blog.csdn.net/qinxiandiqi/article/details/39155593
  [33]: http://wiki.audacityteam.org/wiki/USB_mic_on_Linux
  [34]: http://www.cnblogs.com/cslunatic/p/3227655.html
  [35]: https://www.raspberrypi.org/documentation/usage/audio/
  [36]: https://github.com/alexa/alexa-avs-sample-app/wiki/Raspberry-Pi
  [37]: https://aws.amazon.com/cn/blogs/china/raspberry-alexa/
  [38]: https://github.com/alexa/alexa-avs-sample-app/issues/934
  [39]: https://github.com/alexa/alexa-avs-sample-app/issues/418
  [40]: http://conexant.com/amazon-avs/
  [41]: https://github.com/alexa/alexa-avs-sample-app/wiki/Conexant2Mic-Raspberry-Pi
  [42]: https://www.linuxdashen.com/install-teamviewer-ubuntu-16-04-xenial-xerus
  [43]: http://blog.csdn.net/zht666/article/details/9340633
  [44]: http://www.jianshu.com/p/bcbe916f97e1
  [45]: http://www.cnblogs.com/drfxiaoliuzi/p/4143933.html
  [46]: http://blog.csdn.net/yangzhongxuan/article/details/8444735
  [47]: http://www.metsky.com/archives/257.html
  [48]: http://www.metsky.com/archives/255.html
  [49]: http://blog.csdn.net/cmzsteven/article/details/49049325
  [50]: https://superuser.com/questions/1100810/how-to-solve-low-disk-space-on-boot-in-centos-7
  [51]: http://blog.sina.com.cn/s/blog_45497dfa0100kczc.html
  [52]: http://www.jb51.net/article/56611.htm
  [53]: http://www.cnblogs.com/yjbjingcha/p/7006983.html
  [54]: http://blog.sina.com.cn/s/blog_6e07f1eb0100y85v.html
  [55]: http://mp.weixin.qq.com/s/eC2ZT3DSBPnrkzC7CB672Q##
  [56]: http://www.jb51.net/article/108650.htm
  [57]: https://linux.cn/
  [58]: ./images/2017-08-08_121507.jpg "2017-08-08_121507"
  [59]: http://cn.linux.vbird.org/linux_basic/linux_basic.php