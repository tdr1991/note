# 软件安装常见问题

遇到dpkg问题

![](/Ubuntu14.04/assets/5_1.png)

解决办法

1.$ sudo mv /var/lib/dpkg/info /var/lib/dpkg/info\_old //现将info文件夹更名

2.$ sudo mkdir /var/lib/dpkg/info //再新建一个新的info文件夹

3.$ sudo apt-get update, apt-get -f install

4.$ sudo mv /var/lib/dpkg/info/\* /var/lib/dpkg/info\_old

执行完上一步操作后会在新的info文件夹下生成一些文件，现将这些文件全部移到info\_old文件夹下

5.$ sudo rm -rf /var/lib/dpkg/info //把自己新建的info文件夹删掉

6.$ sudo mv /var/lib/dpkg/info\_old /var/lib/dpkg/info //把以前的info文件夹重新改回名字



