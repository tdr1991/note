# 软件安装问题

## 远程桌面无法打开图形化VScode界面

解决办法：

\# 在家目录创建文件夹并拷贝一个动态库，人后修改其中一行内容

mkdir ~/lib

cp /usr/lib/x86\_64-linux-gnu/libxcb.so.1 ~/lib

sed -i 's/BIG-REQUESTS/\_IG-REQUESTS/' ~/lib/libxcb.so.1

\# set the dynamic loader path to put your library first before executing VS Code

\#设置优先动态库加载路径然后执行命令行打开VScode

LD\_LIBRARY\_PATH=$HOME/lib code

\#如果觉得命令太长可以设置一个别名

alias vscode='LD\_LIBRARY\_PATH=$HOME/lib code'

\#之后每次在命令行输入vscode就能打开VScode

