算法相关的代码都在前面将讲算法的部分已经讲了。  
还有其它的一些改动。  

# monitor

network2增加了过程数据监控功能。  
可以在启动算法时使什么样本的测试数据，监控哪些内容。  
算法结果后，这些监控信息会以list的形式返回，便于画图观察算法的效果。  

# save

`save`函数将生成的模型以json的形式存储到文件中。  