# 系统升级

## 备份

tar -cvpzf /data/backup/Ubuntu.tgz --exclude=/proc --exclude=/lost+found --exclude=/data --exclude=/mnt --exclude=/tmp --exclude=/media --exclude=/home/tdr --exclude=/sys /

“tar”当然就是我们备份系统所使用的程序了。

“cvpfz”是tar的选项，意思是“创建档案文件”、“保持权限”\(保留所有东西原来的权限\)、“使用gzip来减小文件尺寸”。

“Ubuntu.tgz ”是我们将要得到的档案文件的文件名。  
“/data/backup/”备份文件需要存放的目录。

“/”是我们要备份的目录，在这里是整个文件系统。

在 档案文件名“Ubuntu.tgz”和要备份的目录名“/”之间给出了备份时必须排除在外的目录。有些目录是无用的，例如“/proc”、“/lost+ found”、“/sys”。当然，“/data”这个排除在外是因为在它下面挂载的是一块硬盘，如果该目录下还有其他数据另说。如果不把“/mnt”排 除在外，那么挂载在“/mnt”上的其它分区也会被备份。另外需要确认一下“/media”上没有挂载任何东西\(例如光盘、移动硬盘\)，如果有挂载东西， 必须把“/media”也排除在外。

有人可能会建议你把“/dev”目录排除在外，但是我认为这样做很不妥，具体原因这里就不讨论了。

执行备份命令之前请再确认一下你所键入的命令是不是你想要的。执行备份命令可能需要一段不短的时间。

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

有些需要选择的项，但基本上选择yes

## 恢复

在进行恢复系统的操作时一定要小心！如果你不清楚自己在做什么，那么你有可能把重要的数据弄丢，请务必小心！

接着备份的例子。切换到root用户，并把文件“Ubuntu.tgz”拷贝到分区的根目录下。

在 Linux中有一件很美妙的事情，就是你可以在一个运行的系统中恢复系统，而不需要用boot-cd来专门引导。当然，如果你的系统已经挂掉不能启动了， 你可以用Live CD来启动，效果是一样的。你还可以用一个命令把Linux系统中的所有文件干掉，当然在这里我不打算给出这个命令！

使用下面的命令来恢复系统：

\# tar xvpfz Ubuntu.tgz -C /

如果你的档案文件是使用Bzip2压缩的，应该用：

\# tar xvpfj backup.tar.bz2 -C /

注意：上面的命令会用档案文件中的文件覆盖分区上的所有文件。

执行恢复命令之前请再确认一下你所键入的命令是不是你想要的，执行恢复命令可能需要一段不短的时间。

恢复命令结束时，你的工作还没完成，别忘了重新创建那些在备份时被排除在外的目录：

\# mkdir proc

\# mkdir lost+found

\# mkdir mnt

\# mkdir sys

等等

当你重启电脑，你会发现一切东西恢复到你创建备份时的样子了！

查看系统信息

uname -a

lsb\_release -a

