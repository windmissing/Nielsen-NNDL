# 算法一：原始的反向传播算法

1. 对于输入神经元来说，输入x即输出a1  
2. 根据定义依次计算每一层每一个神经元的z和a  
3. 根据公式计算输出神经元的$$\delta^L$$  
4. 根据公式向前依次计算每一层每一个神经元的$$\delta$$  
5. 根据公式计算所有神经元的$$\nabla w$$和$$\nabla b$$  

其中步骤1、2为正向传播，步骤3、4为反向传播。  

# 算法二：反向传播算法 结合 随机梯度下降算法

1. 对于每一个训练样本x，根据反向传播算法计算所有神经元的$$\nabla w^x$$和$$\nabla b^x$$  
2. 对于每一个训练样本x，更新所有的神经元的w和b  
$$
w = w - \frac{\eta}{m}\nabla w^x   \\
b = b - \frac{\eta}{m}\nabla b^x
$$