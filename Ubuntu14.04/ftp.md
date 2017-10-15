# Ubuntu16.04之ftp服务器搭建

## 安装ftp

其实只要安装一个软件vsftpd（very security ftp deamon）

sudo apt-get update

sudo apt-get install vsftpd

## 配置文件说明

/etc/vsftpd.conf ：最主要的配置文件，打开文件后里面有很详细的说明。

/etc/passwd ：都是账号信息，包括ftp账号

![](/Ubuntu14.04/assets/8_1.png)

/etc/vsftpd.chroot\_list ：该文件默认不创建，需要与 /etc/vsftpd.conf 配合使用。

## 匿名用户配置

修改配置文件/etc/vsftpd.conf

anonymous\_enable=YES  \# 匿名用户配置，一般一次配置配置一种类型

local\_enable=NO

修改/etc/passwd

将其家目录修改为想要开放的目录，如上节的截图所示

将家目录修改为：/data/ftp

## 本地用户配置

修改配置文件/etc/vsftpd.conf

anonymous\_enable=NO  \# 匿名用户配置，一般一次配置配置一种类型

local\_enable=YES

local\_root=/data/tdr  \# 将用户登录目录限制在/data/tdr，使其到不了其他目录

\# 为使限制目录生效，需设置下面4条

chroot\_local\_user=YES

chroot\_list\_enable=YES

chroot\_list\_file=/etc/vsftpd.chroot\_list

allow\_writeable\_chroot=YES  \# 很重要，不设置无法登录显示目录

\# 在上面这种设置下，/etc/vsftpd.chroot\_list里的用户表示不受目录限制。如果chroot\_local\_user=NO，

\# 则表 明/etc/vsftpd.chroot\_list的用户是受限制的。

