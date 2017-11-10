## GPU配置问题

一、如果遇到如下问题![](/deeplearning/assets/1-1.png)该问题的意思是显存不够，处理方式可以参考以下步骤解决

首先要知道 tensorflow 默认使用 GPU 的方式，在默认情况下，tensorflow 选择编号最小的 GPU 用来计算，占用所有显卡的显存。

1.通过配置修改显存占用方式

在源程序中，加入以下几行代码

```py
#tensorflow在训练时默认占用所有GPU显存，通过设置 allow_growth，显存分配则按需求增长
    config = tf.ConfigProto()
    config.gpu_options.allow_growth = True
    with tf.Session(config=config) as sess
```

如果方法1不能解决问题，尝试方法2

2.改变batch的大小

若还不能解决问题，则只好修改网络了

3.如果设计的网络是卷积网络，刚好出错的地方又是卷积层，可以通过减少卷积核来缩小网络规模

4.往往一次性将整个测试集放到一个GPU会出现显存不够，一块显卡时，把测试集分成若干子集，循环处理子集，再合并结果，若有多块显卡，则将不同子集分到不同显卡上，再合并结果。

二、多卡运行多模型

如果不加额外的设置，tensorflow默认占用所有显卡，即使使用代码 tf.device\("/gpu:0"\) 指定显卡，或者修改显存占用方式，还是占用了所有卡。此时可以通过命令行设置程序可见的显卡达到使用指定gpu。

在命令行设置临时环境变量，下面一行命令表示当前可见的显卡 是编号为 2和3的显卡，当然也可设置一个或其他，这样程序只会占用显卡2,3。通过命令行nvidia-smi -l 观察到的显卡编号是一致的，但如果通过程序打印的显卡编号还是会从 0 开始编号。

export CUDA\_VISIBLE\_DEVICES=2,3

## 程序问题

![](/deeplearning/assets/1-2.png)

出现该问题可能是因为在一个进程中多次调用了同一个网络模型，这里的提示错误是模型的内核已存在，因为模型定义了变量和命名

空间，此时程序没有结束并没有清空图，这些变量和命名空间仍存在，所以需要重置下，添加以下一行代码：

tf.reset\_default\_graph\(\)

代码解释

![](/deeplearning/assets/1-3.png)

## 不同系统GPU显存占用

1.在windows系统下，通过命令行 nvidia-smi -l 观察到的GPU显存占用是实际程序运行所占用的显存。

![](/deeplearning/assets/1-4.png)

2.在linux系统下，通过命令行 nvidia-smi -l 观察到的GPU显存占用基本整条卡都占用。

![](/deeplearning/assets/1-5.png)

## 不同系统下在模型中打印消息的时间

1.在windows下按照代码先后打印消息

2.在linux下，一次性打印全部消息



