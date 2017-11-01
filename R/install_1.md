# 安装R

系统安装好 R

sudo apt-get install r-base r-base-core -y

下载 R 语言包

sudo apt-get autoremove r-base-core

终端直接输入 R 检查 R 版本

![](/R/assets/1-1.png)

使用 conda 安装R，方便在jupyter中编写R

首先创建一个conda环境，或者在已有环境安装。在该环境安装 R 所需的包。

conda install -c r r-essentials

提示一堆安装的包

![](/R/assets/1-2.png)

安装完成后使用 conda list 查看安装的包

启动 jupyter 是否有 R 环境，可以看到是有 R 环境的

![](/R/assets/1-3.png)

