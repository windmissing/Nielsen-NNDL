# task

![](http://neuralnetworksanddeeplearning.com/images/digits.png)  
识别这串手写数字分两步：  
1. 把一张图切割成几张小图，每张图上一个数字  
![](http://neuralnetworksanddeeplearning.com/images/digits_separate.png)  
2. 识别每张小图上的数字  
![](http://neuralnetworksanddeeplearning.com/images/mnist_first_digit.png)得到5
# task 1 切割

尝试各种切割，切割出的分段得分高，则切割成功。  

# task 2 识别
![](http://neuralnetworksanddeeplearning.com/images/tikz12.png)  
构建三层神经网络：  
输入层：28*28=784个input neuron，为[0,1]的灰度值，0代表白，1代表黑  
输出层：10个，每个代表一个数字。得分最高的output neuron作为预测的结果  
中间层：n个，可以尝试各种n值，本例中取15

## 为什么有10个output neuron，而不是4个？4个二进制足够表达10个数字了。
以第1个output neuron为例：  
如果有10个output neuron，对于第1个neuron，它只要在hidden layer中发现这样的结构(也有可能是其它的结果)，就认为找到0了：  
![](http://neuralnetworksanddeeplearning.com/images/mnist_top_left_feature.png)
![](http://neuralnetworksanddeeplearning.com/images/mnist_other_features.png)  
如果是4个output neuron，很难发现规则在什么情况下第1个neuron是fired。  
也可以通过增加一层hidden layer，将10个数字转化成4个二进制：  
![](http://neuralnetworksanddeeplearning.com/images/tikz13.png)  
