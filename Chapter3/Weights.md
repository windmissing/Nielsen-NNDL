# 当前的weight初始化算法遇到 的问题

考虑只有一个神经元的情况：  

$$
z = \sum_j w_j x_j+b
$$

假设这个神经元有500个输入，$$w,b \sim (\mu=0, \sigma^2=1)$$，
则，$$z \sim (\mu=0, \sigma^2=501)$$  
![](http://windmissing.github.io/images_for_gitbook/Nielsen-NNDL/4.png)  
可以看出z值较大（|z|>1）的概率很大。  
$$
|z|>1 \Rightarrow \sigma(z)接近0或1 \Rightarrow 神经元是饱和的 \Rightarrow 学得慢
$$
因此很大概率，在初始化状态时这个神经元就“学得慢”。  

# 解决方法

这里的“学得慢”和[当前神经网络存在的问题](https://windmising.gitbook.io/nielsen-nndl/introduction-2/crossentropy-dai-jia-han-shu/1)遇到的问题类似。  
但[引入cross-entropy代价函数](https://windmising.gitbook.io/nielsen-nndl/introduction-2/crossentropy-dai-jia-han-shu/2)解决方法只能解决output层神经元在初始化状态下“学得慢”的问题。并不能解决中间层神经元“学得慢”的问题。  

**解决方法：优化weights的初始化算法**，使z的初始值尽量落在区间[-1,1]中。  
如果一个神经元有n个输入，则令weight为高斯分布（$$\mu=0, \sigma^2=\frac{1}{n}$$）的随机值。   
b的初始化算法不变。  
这样神经元在一开始就饱和的可能性会变低。  

# weight不同初始化算法（简称旧、新）的比较  

1. 最终结果差不多  
2. 在开始时候，新算法有明显的优化效果。  
3. 事实上，新算法对最终效果也有提升，见第4章。  

*L2正则化和weights初始化的原理相似，都是要限制weights的大小。*

# 代码

network2.py实现此算法  

```python
self.weights = [np.random.randn(y, x)/np.sqrt(x) 
                for x, y in zip(self.sizes[:-1], self.sizes[1:])]
```

np.random.randn函数的默认分布为（$$\mu=0, \sigma=1$$）的高斯分布。  
将随机值都除以np.sqrt(x)相当于得到的是（$$\mu=0, \sigma=\frac{1}{\sqrt{x}}$$）的高斯分布。  