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

### 定义                       ReLU\(x\) =

\begin{cases}  
0, & {x \ge 0} \  
x, & {x &lt; 0}  
\end{cases}

