# 等式一

证明：$$\delta^L_j = \frac{\partial C}{\partial a^L_j} \sigma'(z^L_j)$$  

$$
\begin{eqnarray}
  \delta^L_j = & \frac{\partial C}{\partial z^L_j}.
\tag{36}  \\
 = & \sum_k \frac{\partial C}{\partial a^L_k} \frac{\partial a^L_k}{\partial z^L_j},
\tag{37} \\
 = & \frac{\partial C}{\partial a^L_j} \frac{\partial a^L_j}{\partial z^L_j}.
\tag{38}  \\
 = & \frac{\partial C}{\partial a^L_j} \sigma'(z^L_j),
\tag{39}
\end{eqnarray}
$$

等式（1）得证

# 等式二  
证明：$$\delta^l = ((w^{l+1})^T \delta^{l+1}) \odot \sigma'(z^l)$$  

$$
\begin{eqnarray}
  \delta^l_j & = & \frac{\partial C}{\partial z^l_j} \tag{40}\\
  & = & \sum_k \frac{\partial C}{\partial z^{l+1}_k} \frac{\partial z^{l+1}_k}{\partial z^l_j} \tag{41}\\ 
  & = & \sum_k \frac{\partial z^{l+1}_k}{\partial z^l_j} \delta^{l+1}_k,
\tag{42} \\
  & = & \sum_k w^{l+1}_{kj}  \delta^{l+1}_k \sigma'(z^l_j).
\tag{45}
\end{eqnarray}
$$

等式二得证

公式（45）说明：  
$$
\begin{eqnarray}
  z^{l+1}_k = \sum_j w^{l+1}_{kj} a^l_j +b^{l+1}_k = \sum_j w^{l+1}_{kj} \sigma(z^l_j) +b^{l+1}_k.
\tag{43} \\
\frac{\partial z^{l+1}_k}{\partial z^l_j} = w^{l+1}_{kj} \sigma'(z^l_j).
\tag{44}
\end{eqnarray}
$$

# 等式三

证明：$$\frac{\partial C}{\partial b^l_j} = \delta^l_j$$  

本章在4个等式的形式和证明过程中，下标有些混乱，给理解公式带来障碍，这里把下标的含义重新申请一下：  
j：当前层的神经元的下标  
k：下一层神经元的下标  
i：上一层神经元的下标  

书上已经写给了$$z^{l+1}_k$$与$$w^{l+1}_{kj}$$、$$b^{l+1}_k$$的关系为：  
$$
\begin{eqnarray}
  z^{l+1}_k = \sum_j w^{l+1}_{kj} a^l_j +b^{l+1}_k
\tag{43}\end{eqnarray}
$$

同理可写出$$z^{l}_j$$与$$w^{l}_{ji}$$、$$b^{l}_j$$的关系为：  
$$
\begin{eqnarray}
  z^{l}_j = \sum_i w^{l}_{ji} a^{l-1}_i +b^{l}_j
\tag{43.1}\end{eqnarray}
$$

$$
\begin{eqnarray}
\frac{\partial C}{\partial b^l_j} & = & \frac{\partial C}{\partial z^l_j} \frac{\partial z^l_j}{\partial b^l_j} = \delta^l_j
\end{eqnarray}
$$

等式三得证

# 等式四

证明：$$\frac{\partial C}{\partial w^l_{jk}} = a^{l-1}_k \delta^l_j$$  

根据等式三中关于下标的定义，等式四应调整为：  
$$
\frac{\partial C}{\partial w^l_{ji}} = a^{l-1}_i \delta^l_j
$$

$$
\begin{eqnarray}
\frac{\partial C}{\partial w^l_{ji}} = \frac{\partial C}{\partial z^l_j} \frac{\partial z^l_j}{\partial w^l_{ji}} = a^{l-1}_k \delta^l_j
\end{eqnarray}
$$

等式三得证