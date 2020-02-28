# 周期神经网络 Recurrent neural networks RNN

在feedback神经网络中，网络是静态的。  
在recurrent神经网络中，网络是动态的：  
一个神经元的行为不肯由它的输入决定，还可以由它上一次的输出以及上一次的输入决定。  

优势：分析会随时间改变的数据，例如演讲、NLP  
在模式识别问题上，CNN不擅长，但RNN擅长。  

# Long short-term memory units (LSTMs)

早期RNN训练非常困难，因为梯度不稳定的问题在RNN中更加严重。  
LSTM用于解决梯度不稳定问题。  

# Deep belief nets, generative models, and Boltzmann machines

根据结果反推出输入数据  
可用于非监督学习