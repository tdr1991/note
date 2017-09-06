# 下载numpy和scipy文件

由于通过pip安装scipy会有问题，需要下载对应的 .whl 文件，网址如下[http://www.lfd.uci.edu/~gohlke/pythonlibs/](http://www.lfd.uci.edu/~gohlke/pythonlibs/)

![](/assets/tensorflow/1.png)

![](/assets/tensorflow/2.png)

下载后的文件如下所示

![](/assets/tensorflow/3.png)

使用pip安装两个包

命令：pip install numpy-1.13.1+mkl-cp36-cp36m-win\_amd64.whl

```
         pip install scipy-0.19.1-cp36-cp36m-win\_amd64.whl
```

# 安装tensorflow-gpu

如果之前安装了cpu的tensorflow需要将其卸载，然后通过pip安装

命令：pip install tensorflow-gpu

测试是否安装成功

打开python环境

输入：import tensorflow as tf

如果没报错，说明安装成功

