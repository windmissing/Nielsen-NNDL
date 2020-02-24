以前，对一个$$w_j$$求偏导的公式为：  
$$
\begin{eqnarray}  \frac{\partial
    C}{\partial w_{j}} \approx \frac{C(w+\epsilon
    e_j)-C(w)}{\epsilon},
\tag{46}\end{eqnarray}
$$
有m个$$w_j$$就要计算m+1次代价函数，也就意味着将整个网络遍历m+1次。  

而反向传播算法能够风里计算所有的$$w_j$$，计算完所有的$$w_j$$只需要将整个遍历2次。  