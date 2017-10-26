# 安装驱动

先执行命令查看是否已安装驱动

nvidia-smi

![](/linuxcuda/assets/1_2.png)

如果提示此信息说明未安装

从官网下载对应版本驱动             [http://www.geforce.cn/drivers](http://www.geforce.cn/drivers)

![](/linuxcuda/assets/1_1.png)

为了避免后面出现 **"You appear to be running an X server" **，限制性以下两条命令

sudo service lightdm stop

sudo init 3

开始安装驱动

cd 至驱动下载存放的目录，执行安装命令

sudo ./NVIDIA-Linux-x86\_64-384.69.run

安装完成后重启

sudo reboot

查看是否安装成功

nvidia-smi

![](/linuxcuda/assets/1-3.png)

出现类似提示说明安装成功

# 安装cuda8

从官网下载对应系统版本的 cuda8  [https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads)

![](/linuxcuda/assets/1-4.png)

cd 至驱动下载存放的目录，执行安装命令

sudo ./cuda\_8.0.61\_375.26\_linux.run

# 安装cudnn7

从官网下载对应系统版本的cudnn7 [https://developer.nvidia.com/rdp/cudnn-download](https://developer.nvidia.com/rdp/cudnn-download)

![](/linuxcuda/assets/1-5.png)

注意：最好下载 .tgz 版本的，在我的电脑上试过 .deb 的，安装不上

![](/linuxcuda/assets/1-6.png)

cd 至cudnn下载存放的目录，执行解压命令

tar -xzvf cudnn-9.0-linux-x64-v7.tgz

拷贝文件和赋权限

sudo cp cuda/include/cudnn.h /usr/local/cuda/include

sudo cp cuda/lib64/libcudnn\* /usr/local/cuda/lib64

sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn\*

# 测试cuda是否安装成功

cd 至 CUDA 8.0 Samples默认安装路径\(即在NVIDIA\_CUDA-8.0\_Samples目录下\)

sudo make all -j4



