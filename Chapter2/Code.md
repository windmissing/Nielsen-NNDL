# `update_mini_batch`

`update_mini_batch(self, mini_batch, eta)`函数实现了“[算法二：反向传播算法 结合 随机梯度下降算法]()”  
实现的过程与描述略不同。  
代码中不是每次求出一个$$\nabla w^x$$和$$\nabla b^x$$就马上更新w和b，而是把所有样本计算出来的$$\nabla w^x$$和$$\nabla b^x$$加起来，最后一次性更新w和b。  
$$
w = w - \frac{\eta}{m}\nabla w^x   \\
b = b - \frac{\eta}{m}\nabla b^x
$$

1. 对于每一个训练样本x，根据反向传播算法计算所有神经元的$$\nabla w^x$$和$$\nabla b^x$$  
```python
delta_nabla_b, delta_nabla_w = self.backprop(x, y)
```
2. 把所有样本计算出来的$$\nabla w^x$$和$$\nabla b^x$$加起来  
```python
nabla_b = [nb+dnb for nb, dnb in zip(nabla_b, delta_nabla_b)]
            nabla_w = [nw+dnw for nw, dnw in zip(nabla_w, delta_nabla_w)]
```  
3. 一次性更新w和b  
```python
self.weights = [w-(eta/len(mini_batch))*nw
                for w, nw in zip(self.weights, nabla_w)]
self.biases = [b-(eta/len(mini_batch))*nb
                for b, nb in zip(self.biases, nabla_b)]
```

# `backprop`  

`backprop(self, x, y)`函数实现了“[算法一：原始的反向传播算法]()”      
1. 对于输入神经元来说，输入x即输出a1  
```python
activations = [x]
```

2. 根据定义依次计算每一层每一个神经元的z和a  
```python
z = np.dot(w, activation)+b
...
activation = sigmoid(z)
```

3. 根据公式计算输出神经元的$$\delta^L$$  
```python
delta = self.cost_derivative(activations[-1], y) * sigmoid_prime(zs[-1])
```
4. 根据公式向前依次计算每一层每一个神经元的$$\delta$$  
```python
sp = sigmoid_prime(z)  # Derivative of the sigmoid function
delta = np.dot(self.weights[-l+1].transpose(), delta) * sp
```

5. 根据公式计算所有神经元的$$\nabla w$$和$$\nabla b$$  
```python
nabla_b[-l] = delta
nabla_w[-l] = np.dot(delta, activations[-l-1].transpose())
```

**以上代码可以以矩阵的方式实现，速度会快很多。**