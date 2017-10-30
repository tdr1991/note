# GPU配置问题

如果遇到如下问题![](/deeplearning/assets/1-1.png)该问题的意思是显存不够，处理方式可以参考以下步骤解决

首先要知道 tensorflow 默认使用 GPU 的方式，在默认情况下，tensorflow 选择编号最小的 GPU 用来计算，占用所有显卡的显存。

1.通过配置修改显存占用方式

在源程序中，加入以下几行代码

\#tensorflow在训练时默认占用所有GPU显存，通过设置 allow\_growth，显存分配则按需求增长

    config = tf.ConfigProto\(\)

    config.gpu\_options.allow\_growth = True

    with tf.Session\(config=config\) as sess

如果方法1不能解决问题，尝试方法2

2.改变batch的大小

若还不能解决问题，则只好修改网络了

3.如果设计的网络是卷积网络，刚好出错的地方又是卷积层，可以通过减少卷积核来缩小网络规模







