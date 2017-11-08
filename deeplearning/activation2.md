# 激活函数

## sigmoid函数

### 定义                          $$f(x) = \frac{1}{1 + e^{-x}}$$

### 图像

![](/deeplearning/assets/2-1.png)

### 优点：

1.Sigmoid函数的输出映射在\(0,1\)之间，单调连续，输出范围有限，优化稳定，可以用作输出层。

2.求导容易。

### 缺点：

1.由于其软饱和性，容易产生梯度消失，导致训练出现问题。

2.其输出并不是以0为中心的。

## tanh函数

### 定义              $$tanh(x) = \frac{1 - e^{-2x}}{1 + e^{-2x}}$$

### 图像

![](/deeplearning/assets/2-2.png)

### 优点：

1.比Sigmoid函数收敛速度更快。

2.相比Sigmoid函数，其输出以0为中心。

### 缺点：

还是没有改变Sigmoid函数的最大问题——由于饱和性产生的梯度消失。

## ReLU函数

### 定义                       ReLU\(x\) = \begin{cases}

0, & {x \ge 0}  \  
x, & {x &lt; 0} \end{cases}$$

### 图像

![](/deeplearning/assets/2-3.png)

优点：

1.相比起Sigmoid和tanh，ReLU\(e.g. a factor of 6 in Krizhevsky et al.\)在SGD中能够快速收敛。例如在下图的实验中，在一个四层的卷积神经网络中，实线代表了ReLU，虚线代表了tanh，ReLU比起tanh更快地到达了错误率0.25处。据称，这是因为它线性、非饱和的形式。

