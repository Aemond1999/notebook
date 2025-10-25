# pytorch and GNN

## torch.nn

### nn.Parameter

```py
#参数
torch.nn.parameter.Parameter(data=None, requires_grad=True)
1.data->tensor:初始化参数
2.requires_grad (bool, optional)->bool
#作用
可训练性：将一个普通张量转换为 Parameter 后，它会被自动添加到模型的参数列表中（model.parameters()），并参与梯度计算和优化。
模块关联：Parameter 通常与 nn.Module 配合使用，用于定义模型的权重或偏置。
```

### 损失函数

```py
#1.交叉熵损失函数
交叉熵函数会自动softmax(input)
CrossEntropyLoss(weight=None, size_average=None, ignore_index=-100, reduce=None, reduction='mean')
- input：最后一层输出
- target：真实标签
- weight：为每个类别设置一个权重
- ignore_index：忽略某个类别
```



### nn.functional

```

```

## pyg

### torch_geometric.data.Data

```py
1.x: 用于存储每个节点的特征，形状是[num_nodes, num_node_features]；
2.edge_index: 用于存储节点之间的边，形状是 [2, num_edges]
3.pos: 存储节点的坐标，形状是[num_nodes, num_dimensions]；
4.y: 存储样本标签。如果是每个节点都有标签，那么形状是[num_nodes, *]；如果是整张图只有一个标签，那么形状是[1, *]；
5.edge_attr: 存储边的特征。形状是[num_edges, num_edge_features]；
6.trian_mask:用于训练节点的数量
```

### GCNConv

```py
#参数
1.in_channels(int):
	输入特征的维度（即每个节点的特征向量长度）。
2.out_channels(int):
	输出特征的维度（即经过GCN层后每个节点的特征向量长度）。
3.improved(bool):
	如果设置为 True，则使用改进的GCN公式,默认值：False。
4.add_self_loops(bool):
	是否在邻接矩阵中添加自环（即每个节点与自己相连）。默认值：True。
	如果输入边索引已经包含自环，则可以将其设置为 False。
5.bias(bool):
	是否在输出变换后添加可学习的偏置项。默认值：True。
6.normalize(bool, optional):
	是否应用对称归一化。默认值：True。
	如果设置为 False，则只进行简单的邻居特征求和（不归一化）。
7.**kwargs:
	其他关键字参数，传递给 torch.nn.Linear层（例如，bias参数已经单独列出，但其他如 device等可以通过这里传递）。
```

### GATv2Conv

```py
# 成员变量
1.in_channels：输入特征维度
2.out_channels：每头注意力的输出维度
3.heads：多头注意力数量
4.concat：多头输出是否拼接，默认为true（若为 False则求平均）
5.negative_slope：LeakyReLU 负斜率，默认为0.2
6.dropout：注意力系数 dropout 概率
7.add_self_loops：是否在图中自动加入每个节点的自环，默认true
8.bias：偏置项，默认为true`

```

### 邻居采样

```
data: 输入的图数据对象（Data或 HeteroData），必须包含节点特征、边索引等信息。
​num_neighbors: 每层采样的邻居数量。例如 [10, 5]表示：
第一层：每个节点采样10个直接邻居。
第二层：对这些邻居再各自采样5个邻居（即二跳邻居）。
​input_nodes: 指定需要计算的起始节点（目标节点），可以是训练/验证/测试集的节点索引。
​batch_size: 每个批次的起始节点数量（如每次训练64个目标节点）
```



## Optimizer

### 使用步骤

```py
import torch.optim as optim
#第一步：选择优化器
optimizer = optim.Adam(model.parameters(), lr=learning_rate, weight_decay=weight_decay)
#第二步：清空梯度
optimizer.zero_grad()
#第三部：优化
optimizer.step()
```

### 优化器

```py
#主要参数：
	1.params：管理的参数组
	2.lr：学习率
	3.momentum：动量系数，贝塔
	4.weight_decay：L2正则化系数
	5.nesterov：是否采用NAG，默认False
#梯度下降优化算法
	1.optim.SGD

	2.optim.Adagrad：自适应学习率梯度下降法

	3.optim.RMSprop：Adagrad的改进

	4.optim.Adadelta：Adagrad的改进

	5.optim.Adam：RMSprop结合Momentum

	6.optim.Adamax：Adam增加学习率上限

	7.optim.SparseAdam：稀疏版的Adam

	8.optim.ASGD：随机平均梯度下降

	9.optim.Rprop：弹性反向传播

	10.optim.LBFGS：BFGS的改进
```







