# 在conda环境下安装jupyter

详情参考 [http://jupyter-notebook.readthedocs.io/en/latest/public\_server.html](http://jupyter-notebook.readthedocs.io/en/latest/public_server.html)

\#激活创建的环境，注意当前的用户，否则使用不了conda

source activate py3

\#安装jupyter

conda install -n py3 -y jupyter

\#创建jupyter配置文件

jupyter notebook --generate-config

\#设置密码，两种方式

1.进入python环境

python

&gt;&gt; from notebook.auth import passwd

&gt;&gt; passwd\(\)

Enter password:

Verify password:

&gt;&gt;: 'sha1:67c9e60bb8b6:9ffede0825894254b2e042ea597d771089e11aed'

特别注意将 hash 码保存下来![](/Ubuntu14.04/assets/9-1.png)2.直接在conda环境设置

jupyter notebook password

![](/Ubuntu14.04/assets/9-5.png)

注意 hash 码的存放位置，貌似无需再配置 “c.NotebookApp.password” 这项。所以推荐使用该方法设置密码。

使用SSL加密通信

openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout mykey.key -out mycert.pem

会在当前目录产生两个文件

![](/Ubuntu14.04/assets/9-2.png)

\#修改jupyter配置文件，在~/.jupyter/下。

gedit ~/.jupyter/jupyter\_notebook\_config.py

\#修改一下几项

\# Set options for certfile, ip, password, and toggle off

\# browser auto-opening

c.NotebookApp.certfile = u'/absolute/path/to/your/certificate/fullchain.pem'

c.NotebookApp.keyfile = u'/absolute/path/to/your/certificate/privkey.pem'

\# Set ip to '\*' to bind on all interfaces \(ips\) for the public server

c.NotebookApp.ip = '\*'

c.NotebookApp.password = u'sha1:bcd259ccf...&lt;your hashed password here&gt;'

c.NotebookApp.open\_browser = False

\# It is a good idea to set a known, fixed port for server access

c.NotebookApp.port = 8888

\#修改默认工作目录

c.NotebookApp.notebook\_dir = u‘/data’

# 安装扩展

conda install -c conda-forge jupyter\_contrib\_nbextensions

如果出现  “libiconv.so.2: cannot open shared object” 问题

1.已存在，创建软连接

ln -s /usr/local/lib/libiconv.so.2 /usr/lib/libiconv.so.2

在执行命令

ldconfig

2.不存在，下载地址  [http://www.gnu.org/software/libiconv/\#downloading](http://www.gnu.org/software/libiconv/#downloading)

tar -zxvf libiconv-1.15.tar.gz

cd libiconv-1.15/

./configure --prefix=/usr/local

make

sudo make install  \#安装提示权限问题加 sudo

sudo ln -s /usr/local/lib/libiconv.so.2 /usr/lib/libiconv.so.2

详情参考 [http://blog.chinaunix.net/uid-25266990-id-2747211.html](http://blog.chinaunix.net/uid-25266990-id-2747211.html)

设置扩展可见

jupyter nbextension enable jupyter\_contrib\_nbextensions

![](/Ubuntu14.04/assets/9-4.png)

# 通过ssh远程使用jupyter

1.在远程服务器，启动jupyter服务

如果是用 conda 安装的 jupyter ，比如安装在 py 3 的环境下，需要先激活环境（source activate py3），最好放到后台运行，否则终端需要一直开着，也可将这些命令写入一个脚本。

jupyter notebook --no-brower --port=8888

命令写入脚本 jupyter.sh

vim jupyter.sh

![](/Ubuntu14.04/assets/9-6.png)

浏览器登陆后的显示目录是当前的目录如果没有在配置文件中修改工作目录

2.本地终端启动ssh

ssh -N -f -L localhost:8888:localhost:8888 remote\_user@remote\_host

其中： -N 告诉SSH没有命令要被远程执行； -f 告诉SSH在后台执行； -L 是指定port forwarding的配置，远端端口是8888，本地的端口号的8888。remote\_user@remote\_host 用实际的远程帐户和远程地址替换

3.打开本地浏览器，输入地址  [http://localhost:8888/](http://localhost:8888/)

进入后，需要输入刚才设置的密码

或者启动 jupyter 界面显示的  token

![](/Ubuntu14.04/assets/9-3.png)

4.命令写入脚本

因为本地系统是windows 10，所以使用 git 操作命令

vim jupyter.sh

内容如下

\#!/bin/bash

ssh -N -f -L localhost:8888:localhost:8888 username@ip

命令行输入

./jupyter.sh

如果没有执行权限，则会提示无 bash 命令。此时有两种方法解决

a.bash jupyter.sh

b.给脚本添加执行权限

chmod u+x jupyter.sh

除了用bash执行脚本，也可用sh执行，设置与bash一样。

脚本执行时可能需要手动输入密码，如需无密码登录，可以参考

[Ubuntu14.04/ssh.md](/Ubuntu14.04/ssh.md)

