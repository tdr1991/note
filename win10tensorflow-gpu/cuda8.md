# 检查电脑安装的GPU型号

![](/assets/cuda/1.png)![](/assets/cuda/2.png)右键  此电脑-》管理-》设备管理器-》显示适配器

如果电脑有NVIDIA的GPU会有如上的类似显示，前提是安装了显卡驱动。

# 下载cuda toolkits8和cudnn7

# [https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads)![](/assets/cuda/3.png)

# [https://developer.nvidia.com/rdp/cudnn-download](https://developer.nvidia.com/rdp/cudnn-download)![](/assets/cuda/4.png)

下载后的文件如下所示![](/assets/cuda/5.png)

# 安装cuda

1.正常安装cuda\_8.0.61\_win10.exe

2.解压cudnn-8.0-windows10-x64-v7.zip

3.将cudnn中的以下目录

![](/assets/cuda/6.png)

拷贝覆盖 C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v8.0 的目录

![](/assets/cuda/7.png)

4.在cmd下执行 nvcc -V 检查是否安装成功

![](/assets/cuda/8.png)

5.添加环境变量

如果要在命令行使用nvidia-smi命令，需要在环境变量中添加该程序的路径，添加方法如下：

右键点击  “我的电脑”-》“属性"-&gt;”高级系统设置“-》”环境变量“-》”系统变量“-》”Path“-》”编辑“-》”新建“

在新建的那一栏填入路径 “C:\Program Files\NVIDIA Corporation\NVSMI”，安装路径不同的话路径是不一样的，找到nvidia-smi所在的目录就对了。

6.出现的问题![](/assets/cuda/10.png)![](/assets/cuda/9.png)出现cudnn版本不匹配，我这里下载的是v7版本的cudnn，按照上面的提示匹配的版本应该是v6版本，下载v6版本即可解决问题。

