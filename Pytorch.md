# Pytorch

## 创建数据集

### dataset

```py
#概念
torch.utils.data.dataset是抽象类可以用来创建数据集
#创建dataset
1.继承dataset
2.重写三个函数:
  __init__   获取数据
  __len__	   返回数据集长度
  __getitem__输入index 返回一个数据和标签
```

### dataloader

```
#创建
dataset (必需): 用于加载数据的数据集，通常是torch.utils.data.Dataset的子类实例。
batch_size (可选): 每个批次的数据样本数。默认值为1。
shuffle (可选): 是否在每个周期开始时打乱数据。默认为False。
num_workers (可选): 用于数据加载的子进程数量。默认为0，意味着数据将在主进程中加载。
```

## Tensor

### 创建张量

```python
1.从 Python 列表或 NumPy 数组创建张量
	torch.tensor(data)
2.创建一个全为零的张量
	torch.zeros(size)
3.创建一个全为 1 的张量
	torch.ones(size)
4.创建一个未初始化的张量
	torch.empty(size)
5.创建一个服从均匀分布的随机张量，值在 [0, 1)
  torch.rand(size)
5.创建一个服从均匀分布的随机张量，值在 [start, end)
	torch.randint(start,end,size)
6.创建一个服从正态分布的随机张量，均值为 0，标准差为 1。
  torch.randn(size)
7.创建一个一维序列张量
  torch.arange(start, end, step)
8.创建一个在指定范围内等间隔的序列张量
  torch.linspace(start, end, steps)
9.创建一个单位矩阵
  torch.eye(size)
10.将 NumPy 数组转换为张量
  torch.from_numpy(ndarray)      
11.稀疏张量
  坐标=torch.Tensor([[x,x,x],[x,x,x]])
  值=torch.Tensor([x,x,x])
  稀疏张量=torch.spare_coo_tensor(坐标,值,size)
```

### 张量的属性

```python
1.shape	  					获取张量的形状	
2.size()						获取张量的形状	
3.dtype	 						获取张量的数据类型
4.device						查看张量所在的设备 (CPU/GPU)	
5.dim()							获取张量的维度数	
6.requires_grad			是否启用梯度计算	
7.numel()						获取张量中的元素总数	
8.is_cuda						检查张量是否在 GPU 上	
9.T									获取张量的转置（适用于 2D 张量）	
10.item()						将单元素张量的值变成标量	
11.is_contiguous()	检查张量是否连续存储	
12.view(shape)      reshape
```

### 张量操作

```python
1.torch.matmul(x, y)		矩阵乘法
2.torch.dot(x, y)				向量点积（仅适用于 1D 张量）
3.torch.sum(x)					求和
4.torch.mean(x)					求均值
5.torch.max(x)					求最大值
6.torch.min(x)					求最小值
7.torch.argmax(x, dim)	返回最大值的索引（指定维度
8.torch.softmax(x, dim)	计算 softmax（指定维度）
9.x.reshape(shape)   
10.x.unsqueeze(dim)			在指定维度添加一个维度。
11.x.squeeze(dim)				去掉指定维度为 1 的维度。
12.torch.cat((x, y), dim)	按指定维度连接多个张量。
13.x.flatten()           将张量展平成一维
14.x.numpy()	           将张量转换为 NumPy 数组（仅限 CPU 张量）
```

### 比较/排序运算

```py
1.torch.equal(tensor1,tensor2) 	如果tensor1和tensor2有相同的size且每个元素都相等返回Ture
2.torch.eq/ge/gt/lt/le(tensor1,tensor2) 
3.torch.sort(tensor,dim,descending) 
4.torch.topk(tensor,k,dim) 			按指定维度返回k个最大值及其索引
5.torch.kthvalue(tensor,k,dim)	按指定维度返回k个最小值及其索引
6.torch.isfinite(tensor)				判断tensor是否有界
7.torch.isinf(tensor)
8.torch.isnan(tensor)
```

### 统计学相关函数

```py
1.torch.mean(tensor)
2.torch.sum(tensor)
3.torch.prod(tensor)	 		计算所有元素之积
4.torch.max(tensor)
5.torch.min(tensor)
6.torch.argmax(tensor) 		返回最大值的索引
7.torch.argmin(tensor)
8.torch.std(tensor)
9.torch.var(tensor) 			方差
10.torch.median(tensor)
11.torch.mode(tensor) 			众数
12.torch.bincount(tensor)	 返回每个值的频数
```

### 范数

```py
1.torch.dist(tensor1,tensor2,p) 计算两个向量之间的距离
2.torch.norm()                  计算向量的长度
```

### 张量裁剪

```py
clamp(A,B) 将张量的值限制在A与B之间
```

### 索引与数据筛选

```py
1.torch.where(condition,tensor1,tensor2) 按照条件从tensor1和tensor2中选择满足条件的元素组成新tensor
2.torch.gather(input,dim,index) 在指定维度上按照索引输出tensor
2.torch.index_select(input,dim,index) 在指定维度上按照索引输出tensor
3.torch.take(input,index)将输入看成一维张量，按照index输出tensor
4.torch.nonzero(input)输出非0元素的坐标
```

### 拼接

```py
1.torch.cat((a,b),dim)
2.torch.stack((a,b),dim)
```

### 拆分

```py
1.torch.chunk(tensor,chunks,dim)						按照指定维度切成chunks等份
2.torch.split(tensor,split_size_or_list,dim)根据split_size_or_list进行拆分
```

### 改变张量形状

```py
1.torch.reshape(tensor,shape)
2.torch.transpose(input,dim1,dim2) 交换两个维度
3.torch.squeeze(input) 去除维度大小为1的维度
4.torch.inbind(input,dim)去除指定维度
```

### autpgrad

```
1.torch.autograd.backward(...)
-tensor:用于计算梯度
-grad_tensor:若tensor是一个张量，需要提供一个size一样的tensor
-
```

