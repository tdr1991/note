# 在conda环境下安装jupyter

详情参考 [http://jupyter-notebook.readthedocs.io/en/latest/public\_server.html](http://jupyter-notebook.readthedocs.io/en/latest/public_server.html)

\#激活创建的环境，注意当前的用户，否则使用不了conda

source activate py3

\#安装jupyter

conda install -n py3 -y jupyter

\#创建jupyter配置文件

jupyter notebook --generate-config

\#进入python环境，设置密码

python

&gt;&gt; from notebook.auth import passwd

&gt;&gt; passwd\(\)

Enter password:

Verify password:

&gt;&gt;: 'sha1:67c9e60bb8b6:9ffede0825894254b2e042ea597d771089e11aed'

特别注意将 hash 码保存下来![](/Ubuntu14.04/assets/9-1.png)使用SSL加密通信

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

# 通过ssh远程使用jupyter

1.在远程服务器，启动jupyter服务

jupyter notebook --no-brower --port=8888

2.本地终端启动ssh

ssh -N -f -L localhost:8888:localhost:8888 remote\_user@remote\_host

其中： -N 告诉SSH没有命令要被远程执行； -f 告诉SSH在后台执行； -L 是指定port forwarding的配置，远端端口是8888，本地的端口号的8888。remote\_user@remote\_host 用实际的远程帐户和远程地址替换

3.打开本地浏览器，输入地址  [http://localhost:8888/](http://localhost:8888/)

进入后，需要输入刚才设置的密码

或者启动 jupyter 界面显示的  token

![](/Ubuntu14.04/assets/9-3.png)



