反向传播算法的目标：**求出代价函数C在任意w、b处的偏导$$\partial C / \partial w$$和$$\partial C / \partial b$$**。  

反向传播函数对代价函数有两个假设，以第一章所使用的二次代价函数为例：  
$$
\begin{eqnarray}
  C = \frac{1}{2n} \sum_x \|y(x)-a^L(x)\|^2,
\tag{26}\end{eqnarray}
$$

# 假设一

假设一：代价函数C可以写成每个样本的代价函数之和的形式  
$$
C = \frac{1}{n} \sum_x C_x
$$
例如对于公式26来说，有  
$$
C_x = \frac{1}{2} \|y-a^L \|^2 \tag{1}
$$

问：为什么会有这样的假设？
答：因为反向传播算法是针对每个样本单独计算偏导的。  

# 假设二

假设二：代价函数$$C_x$$可以写成神经元视角的形式。  
*神经元视角是我发明的词，我不知道怎么表达这种形式。参见[link]()*

例如公式（1）可以写成  
$$
\begin{eqnarray}
  C = \frac{1}{2} \|y-a^L\|^2 = \frac{1}{2} \sum_j (y_j-a^L_j)^2,
\tag{27}\end{eqnarray}
$$