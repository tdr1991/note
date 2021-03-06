# 激活函数

## sigmoid函数

### 定义

### $$sigmoid(x) = \frac{1}{1 + e^{-x}}$$

### 图像

![](/deeplearning/assets/2-1.png)

### 优点：

1.Sigmoid函数的输出映射在\(0,1\)之间，单调连续，输出范围有限，优化稳定，可以用作输出层。

2.求导容易。

### 缺点：

1.由于其软饱和性，容易产生梯度消失，导致训练出现问题。

2.其输出并不是以0为中心的。

## tanh函数

### 定义

### $$tanh(x) = \frac{1 - e^{-2x}}{1 + e^{-2x}}$$

### 图像

![](/deeplearning/assets/2-2.png)

### 优点：

1.比Sigmoid函数收敛速度更快。

2.相比Sigmoid函数，其输出以0为中心。

### 缺点：

还是没有改变Sigmoid函数的最大问题——由于饱和性产生的梯度消失。

## softmax函数

### 定义

### $$softmax(x_i) = \frac{e^{x_i}}{\sum_{j=1}^ne^{x_j}}$$

### 图像

softmax的每个神经元输出都为正，且它们的和为1，可以将它看成一个概率分布。

## ReLU函数

### 定义

$$ReLU(x) = 
\begin{cases}
0, & {x \ge 0} \\
x, & {x < 0}
\end{cases}$$

### 图像

![](/deeplearning/assets/2-3.png)

### 优点：

1.相比起Sigmoid和tanh，ReLU在SGD中能够快速收敛。

2.Sigmoid和tanh涉及了很多很expensive的操作（比如指数），ReLU可以更加简单的实现。

3.有效缓解了梯度消失的问题。

4.在没有无监督预训练的时候也能有较好的表现。

5.提供了神经网络的稀疏表达能力。

### 缺点：

随着训练的进行，可能会出现神经元死亡，权重无法更新的情况。如果发生这种情况，那么流经神经元的梯度从这一点开始将永远是0。也就是说，ReLU神经元在训练中不可逆地死亡了。

## LReLU、PReLU与RReLU函数 {#lreluprelu与rrelu}

### LReLU、PReLU定义

$$f(x) = \begin{cases}
x, & {x > 0} \\ \alpha(x), & {x \le 0} \end{cases}$$

### 图像

![](/deeplearning/assets/2-4.png)

### LReLU

当ai比较小而且固定的时候，我们称之为LReLU。LReLU最初的目的是为了避免梯度消失。但在一些实验中，我们发现LReLU对准确率并没有太大的影响。很多时候，当我们想要应用LReLU时，我们必须要非常小心谨慎地重复训练，选取出合适的a，LReLU的表现出的结果才比ReLU好。因此有人提出了一种自适应地从数据中学习参数的PReLU。

### PReLU

PReLU是LReLU的改进，可以自适应地从数据中学习参数。PReLU具有收敛速度快、错误率低的特点。PReLU可以用于反向传播的训练，可以与其他层同时优化。

