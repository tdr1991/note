# 安装多版本python

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



