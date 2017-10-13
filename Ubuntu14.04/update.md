# 系统升级

## 备份

tar -cvpzf /data/backup/Ubuntu.tgz --exclude=/proc --exclude=/lost+found --exclude=/data --exclude=/mnt --exclude=/tmp --exclude=/media --exclude=/home/tdr --exclude=/sys /

## 升级

如果你的系统中没有安装update-manager-core软件包，安装它

sudo apt-get install update-manager-core

编辑文件/etc/update-manager/release-upgrades：

sudo vim /etc/update-manager/release-upgrades

如果你的系统是Ubuntu 14.04 Server，设置Prompt=lts

sudo apt-get update && sudo apt-get dist-upgrade

重启系统

sudo reboot

如果使用ssh登录服务器升级，建议使用screen，防止SSH连接断开。 

安装screen，启动screen，升级Ubuntu：

 sudo apt-get install screen

screen

sudo do-release-upgrade -p



