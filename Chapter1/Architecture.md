![](http://neuralnetworksanddeeplearning.com/images/tikz11.png)  
神经网络分为：输入层、输出层、中间层(hidden layer)  

**输入层**： 
每个特征作为一个输入神经元。  
取值为[0,1]  
**输出层**：  
输出值为(0,1)  
输出值 < 0.5代表否  
输出值 > 0.5代表是  
**中间层**：  
中间层的设计需要要一些技巧，如果网络深度与训练时间之间的平衡。  
本书后面会这个话题。  

**feedforward神经网络**：这一层的输出是下一层的输入，中间没有循环  
**recurrent(复发的)神经网络**：网络中有循环。这种情况下的神经元只在特征条件下才会fire。  

recurrent不如feedforward有影响力。但recurrent更接近大脑的工作方式。  
本书仅讲解feedforward神经网络。