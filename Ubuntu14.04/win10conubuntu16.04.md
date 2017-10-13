# win10远程控制Ubuntu16.04

## 打开终端，安装xrdp、vncserver

sudo apt-get install xrdp vnc4server xbase-clients

如果出现以下错误，按步骤解决

安装错误：“E: Unmet dependencies.”  
原因：非正常停止apt-get install \*

错误提示：E: Unmet dependencies. Try 'apt-get -f install' with no packages \(or specify a solution\)

解决方法：sudo apt-get --fix-broken install

## 在搜索框搜索desktop sharing

![](/Ubuntu14.04/assets/2_1.png)

![](/Ubuntu14.04/assets/2_2.png)

## 安装dconf-editor，取消权限限制

sudo apt-get install dconf-editor

在搜索框搜索dconf-editor

![](/Ubuntu14.04/assets/2_3.png)

dconf-editor是一个注册表编辑器

设置： org &gt; gnome &gt; desktop &gt; remote-access，取消“ require-encryption”

![](/Ubuntu14.04/assets/2_4.png)

如果使用的是xfce桌面

sudo apt-get install xubuntu-desktop

echo "xfce4-session" &gt; ~/.xsession

sudo service xrdp restart

然而发现tab键不能用了，解决方法如下：$ xfwm4-settings，找到keyboard，

将switch windows for same application项clear一下

![](/Ubuntu14.04/assets/2_5.png)

## 使用vcnserver 和 vncviwer

### ubuntu配置

查看安装的桌面

ls /usr/share/xsessions/

如果设置默认桌面，编辑 /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf，可以看到里面有个user-session字样，等号后面就是对应的桌面环境

![](/Ubuntu14.04/assets/2_7.png)

使用dpkg -l查看安装的程序，后面命令是过滤筛选

dpkg -l \| grep cinnamon

![](/Ubuntu14.04/assets/2_6.png)

在命令行输入vncserver

如果用户首次启动，会提示输入密码，然后会给一个默认的显示编号

也可在命令中指定

vncserver :3

可以通过命令修改密码

vncpasswd

然后在家目录下生成 .vnc目录

先把服务杀掉

vncserver -kill :3

修改文件 /home/user/.vnc/xstartup文件，只有cinnamon-session 有用，其他都没不知道为啥

![](/Ubuntu14.04/assets/2_8.png)

启动服务

vncserver :3

### 本地远程登录

下载vnc viwer

[https://www.realvnc.com/en/connect/download/viewer/](https://www.realvnc.com/en/connect/download/viewer/)

安装登录

输入IP及显示编号

1.2.3.4:3

登陆后界面

![](/Ubuntu14.04/assets/2_9.png)







