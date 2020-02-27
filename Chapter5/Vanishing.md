vanishing gradient problem：加入多层神经元后发现，靠前层神经元的梯度远小于靠后神经元的梯度。  
![](http://neuralnetworksanddeeplearning.com/images/training_speed_4_layers.png)  
与之相对的梯度爆炸问题。  
exploding gradient problem：靠前层神经元的梯度远大于靠后神经元的梯度。 
总之，深度神经网络的梯度不稳定，要么vanishing，要么exploding。  

问：梯度小是因为参数已经接近目标不需要调整了吗？  
答：不是。因为初值是随机初始化的，不太可能一开始就接近目标了。  
[?]还有一句没看懂  
> The random initialization means the first layer throws away most information about the input image.


