# 安装多版本python

## 在本地安装

Ubuntu默认安装python2.7

1.查看当前python版本

python --version

![](/Ubuntu14.04/assets/3_1.png)

2.安装前进行一些更新

sudo add-apt-repository ppa:fkrull/deadsnakes

sudo apt-get update

3.安装python3.6

sudo apt-get install python3.6

默认安装最新的3.6.2版本

![](/Ubuntu14.04/assets/3_2.png)

4.修改软连接

查看安装的python

![](/Ubuntu14.04/assets/3_3.png)

删除2.7版本的软连接

rm  /usr/bin/python

![](/Ubuntu14.04/assets/3_4.png)

创建3.6软连接

ln -s /usr/bin/python3.6 /usr/bin/python

![](/Ubuntu14.04/assets/3_5.png)

查看版本

![](/Ubuntu14.04/assets/3_6.png)

5.python3安装的pip命令使用时pip3

pip3 list

![](/Ubuntu14.04/assets/3_7.png)

## 使用Miniconda安装

Miniconda下载    [https://conda.io/miniconda.html](https://conda.io/miniconda.html)

根据系统自行选择相应版本

下载的文件是一个.sh文件

![](/Ubuntu14.04/assets/3_8.png)

注意当前的用户状态，不同用户安装的conda是不能互相访问的

然后使用命令  bash ./Miniconda3-latest-Linux-x86\_64.sh

安装过程出现是否添加环境变量，选择yes如下

![](/Ubuntu14.04/assets/3_9.png)

安装完成后如果需要立即生效需执行更新命令

source  ~/.bashrc

![](/Ubuntu14.04/assets/3_10.png)

删除Miniconda

rm -rf ~/miniconda

rm -rf ~/.condarc ~/.conda ~/.continuum

删除安装的根目录

rm -rf /home/ubuntu/miniconda3/

![](/Ubuntu14.04/assets/3_11.png)

创建python环境

conda create --name py3 python=3

![](/Ubuntu14.04/assets/3_12.png)

激活环境

source activate py3

![](/Ubuntu14.04/assets/3_13.png)

退出环境

source deactivate

如果要在Ubuntu显示matplotlib画的图形

sudo apt-get install tk-dev

在python源文件添加以下两条语句

import matplotlib as mpl

mpl.use\("TkAgg"\)   \#默认使用Agg为后端，但是Agg没有绘图能力

