本章使用nerwork3.py和theano库

# 最开始的神经网络

**网络结构**

||||
|---|---|---|
|输入层|输入神经元|784|
|中间层|sigmoid神经元，完全连接|100||
|输出层|softmax神经元，log-likelihood代价函数|10|

无正则化  

**准确率**
97.8%

# 加入一层带pooling的卷积层

**目的**：  
减少参数，简化问题  

**网络结构**

![](http://neuralnetworksanddeeplearning.com/images/simple_conv.png)  

||||
|---|---|---|
|输入层|输入神经元|28 * 28|
|卷积层|local receptive fields = 5 * 5<br>feature map = 20|20 * 24 * 24|
|pooling层|pooling window = 2 * 2|20 * 12 * 12|
|中间层|sigmoid神经元，完全连接|100|
|输出层|softmax神经元，log-likelihood代价函数|10|

无正则化

**准确率**

98.78 效果明显

# 再加入一层带pooling的卷积层

**网络结构**

||||
|---|---|---|
|输入层|输入神经元|28 * 28|
|卷积层1|local receptive fields = 5 * 5<br>feature map = 20|20 * 24 * 24|
|pooling层1|pooling window = 2 * 2|20 * 12 * 12|
|卷积层2|local receptive fields = 5 * 5<br>feature map = 40|40 * 8 * 8|
|pooling层2|pooling window = 2 * 2|40 * 4 * 4|
|中间层|sigmoid神经元，完全连接|100|
|输出层|softmax神经元，log-likelihood代价函数|10|

无正则化

**准确率**

99.06 效果明显

卷积层2的输入为12 * 12的图像，每一个像素代表原始图像中这个位置是否存在某个局部特征。  
12 * 12的图像是原始图像抽象和压缩过的信息，但仍存在图像的空间结构，因此继续使用卷积神经网络是有意义的。  

pooling2层的输出是20个pooling，相当于卷积层2有20个不同的feature，这个20和后面的40是完全连接的（可以这么理解吗？[?]）

# 中间层神经元改为rectified linear神经元

**目的**：  
加速学习  

**网络结构**

||||
|---|---|---|
|输入层|输入神经元|28 * 28|
|卷积层1|local receptive fields = 5 * 5<br>feature map = 20|20 * 24 * 24|
|pooling层1|pooling window = 2 * 2|20 * 12 * 12|
|卷积层2|local receptive fields = 5 * 5<br>feature map = 40|40 * 8 * 8|
|pooling层2|pooling window = 2 * 2|40 * 4 * 4|
|中间层|rectified linear神经元，完全连接|100|
|输出层|softmax神经元，log-likelihood代价函数|10|

无正则化

**准确率**

99.23 有效果

为什么用rectified linear神经元效果更好？作者也不知道。  

# 增加训练样本

网络结构不变，训练样本的每张图像向上下左右各移1个像素得到新的图像。  
样本集的数量是原来的5倍。  

**准确率**

99.37 一点点的提升

# 增加一个完全连接的中间层

**网络结构**

||||
|---|---|---|
|输入层|输入神经元|28 * 28|
|卷积层1|local receptive fields = 5 * 5<br>feature map = 20|20 * 24 * 24|
|pooling层1|pooling window = 2 * 2|20 * 12 * 12|
|卷积层2|local receptive fields = 5 * 5<br>feature map = 40|40 * 8 * 8|
|pooling层2|pooling window = 2 * 2|40 * 4 * 4|
|中间层1|rectified linear神经元，完全连接|100|
|中间层2|rectified linear神经元，完全连接|100|
|输出层|softmax神经元，log-likelihood代价函数|10|

**准确率**

99.43 一点点的提升

# 引入drop out正则化技术

**目的**：  
减少过拟合  

**网络结构**

||||
|---|---|---|
|输入层|输入神经元|28 * 28|
|卷积层1|local receptive fields = 5 * 5<br>feature map = 20|20 * 24 * 24|
|pooling层1|pooling window = 2 * 2|20 * 12 * 12|
|卷积层2|local receptive fields = 5 * 5<br>feature map = 40|40 * 8 * 8|
|pooling层2|pooling window = 2 * 2|40 * 4 * 4|
|中间层1|rectified linear神经元，完全连接|1000，50 drop out|
|中间层2|rectified linear神经元，完全连接|1000，50 drop out|
|输出层|softmax神经元，log-likelihood代价函数|10|

问：为什么只对完全链接的神经元做drop out？
答：因为卷积层的weight是共享的，使得它必须学习整个图像， 不会困于局部。  

**准确率**

99.60 有实质性的提升

# 集成学习

创建5个同样的网络，因为初值是随机的，所以训练出来的是5个不同的模型。  
让5个模型对同一个样本做预测，然后投票

**准确率**

99.67