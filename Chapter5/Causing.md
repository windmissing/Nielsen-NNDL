# 梯度消失问题

考虑最简单的深度神经网络：  
![](http://neuralnetworksanddeeplearning.com/images/tikz37.png)  

计算b1的梯度为：  
$$
\begin{eqnarray}
\frac{\partial C}{\partial b_1} = \sigma'(z_1) w_2 \sigma'(z_2) \ldots
\sigma'(z_4) \frac{\partial C}{\partial a_4}.
\tag{121}\end{eqnarray}
$$

由于w被初始化为均值为0方差为1的随机数，|w|有很大可能落小于1。  
再看$$\sigma'(z)$$的图形：  
![](http://windmissing.github.io/images_for_gitbook/Nielsen-NNDL/7.png)  
$$\sigma'(z)$$的最大值为1/4。  

![](http://neuralnetworksanddeeplearning.com/images/tikz39.png)  
将b1的梯度与b3的梯度做比较，就能看出为什么梯度越来越小了。

# 梯度爆炸问题

仔细观察公式（121），如果将w设置得很大并巧妙地设置b，使得$$w_j\sigma'(z_j)$$变大，这个问题就变成了梯度爆炸问题了。  

# 梯度不稳定问题

不管梯度消失还是梯度爆炸，根本原因是梯度的连乘。  

这里是每一层只有一个神经元的例子。  
在复杂的深度神经网络中的结果是相同的。  