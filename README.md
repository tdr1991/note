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

