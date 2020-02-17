# 什么是感知机 perceptron

![](http://neuralnetworksanddeeplearning.com/images/tikz0.png)
感知机有不少于1个的输入，只有1个输出。  
输入输出都是二元(binary)的。  
w为权重，可以是任意实数。  
b为偏移，代表有多空间使输入为1。  
$$
\begin{eqnarray}
  \mbox{output} = \left\{ 
    \begin{array}{ll} 
      0 & \mbox{if } w\cdot x + b \leq 0 \\
      1 & \mbox{if } w\cdot x + b > 0
    \end{array}
  \right.
\tag{2}\end{eqnarray}
$$

# 感知机的作用

1. 做决策  
2. 实现NAND gate  
用感知机组成的网络，可以利用NAND gate的性质表达任意的circuit。  
但感知机和NAND gate比，它能自动调参，即具有学习能力。  
将具有学习能力的感知机组成网络，可以实现比传统的circuit更复杂的东西。