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

