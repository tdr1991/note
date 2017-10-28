# 本地通过ssh登录远程linux

因为本地系统是windows 10，所以使用 git 操作命令。git集成了mingW，mingW 提供了一套简单方便的Windows下的基于GCC 程序开发环境。MinGW 收集了一系列免费的Windows 使用的头文件和库文件；同时整合了GNU \( [http://www.gnu.org/](http://www.gnu.org/) \)的工具集，特别是GNU 程序开发工具，所以可以在windows下使用linux系统中使用的那些命令。

## 首先了解命令安装的位置

右键鼠标点击 git bash here

进入ming64系统后的当前目录就是桌面

![](/Ubuntu14.04/assets/10-1.png)

cd 根目录，该根目录就是 git 安装的目录

cd /

![](/Ubuntu14.04/assets/10-2.png)

所有能够执行的命令就在 /bin 目录下，以下截图只显示了 sh 开头的命令

![](/Ubuntu14.04/assets/10-3.png)

## 使用sh执行登录脚本

vim jupyter.sh

内容如下

\#!/bin/sh

ssh username@ip

命令行输入

./jupyter.sh

如果没有执行权限，则会提示无sh 命令。此时有两种方法解决

a.sh jupyter.sh

b.给脚本添加执行权限

chmod u+x jupyter.sh

除了用sh执行脚本，也可用bash执行，设置与sh一样。

此时执行脚本后需要手动输入密码，如需无密码登录，则要配置秘钥

1.生成秘钥

ssh-keygen --t rsa

默认会在用户目录下生成两个文件，id\_rsa 为私钥，id\_rsa.pub 为公钥

![](/Ubuntu14.04/assets/10-4.png)

2.将id\_rsa.pub公钥文件传至远程服务器家目录的 .ssh 目录下，如何传送文件参考 [Ubuntu14.04/file.md](/Ubuntu14.04/file.md)，并修改其名为 authorized\_keys 。

scp /c/Users/username/.ssh/idrsa.pub remote\_username@remote\_ip:/home/remote\_username/.ssh/authorized\_keys 

