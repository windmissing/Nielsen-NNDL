# 感知机的缺陷

要使网络有学习的能力，就要求神经元满足以下特点：  
权重和偏移的轻微改变，导致网络最终输出的轻微改变。  
![](http://neuralnetworksanddeeplearning.com/images/tikz8.png)  
但感知机神经元不满足这个特点：  
权重和偏移的轻微改变，可能会使它自己的输出翻转，导致网络的最终输出不可控。  

# 改进：sigmoid神经元

sigmoid神经元与感知机神经元类似，且满足网络对神经元的要求。  

||感知机神经元|sigmoid神经元|
|---|---|---|
|输入|0，1|[0,1]|
|输出|0,1|(0,1)|
|w, b|任意实数|任意实数|
|function|w*x+b|$$\sigma(w\cdot x+b)$$<br>$$\sigma(z)=\frac{1}{1+e^{-z}}$$

# $$\sigma$$函数

[link](https://windmising.gitbook.io/mathematics-basic-for-ml/gai-shuai-lun/functions)  
$$\sigma(z)=\frac{1}{1+e^{-z}}$$
![](http://windmissing.github.io/images_for_gitbook/mathematics_basic_for_ML/2.png)  
它是感知机的平滑版本。  
这就意味着**小的改变$$\Delta w$$和$$\Delta b$$会导致小的改变$$\Delta$$output**   
$$
\begin{eqnarray} 
  \Delta \mbox{output} \approx \sum_j \frac{\partial \, \mbox{output}}{\partial w_j}
  \Delta w_j + \frac{\partial \, \mbox{output}}{\partial b} \Delta b,
\tag{5}\end{eqnarray}
$$
同时，$$\Delta$$output与$$\Delta w$$和$$\Delta b$$呈线性关系。这也意着**可以通过选择$$\Delta w$$和$$\Delta b$$得到想要的$$\Delta$$output**。  

# 激活函数 activation function

sigmoid神经元中的$$\sigmoid(z)$$就是激活函数。  
激活函数通常用f(*)表示。  
可以选择不同的激活函数，这会导致公式（5）是的偏导部分不同。  
$$\sigmoid(z)$$是最常用的激活函数。因为它在求偏导方法非常友好。  