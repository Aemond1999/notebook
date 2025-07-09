## Numpy

### ndarray

```python
# ndarry：N-dimensional array的缩写，属于一个Python的类
# 特点：只能存储相同数据类型的元素，每个维度的元素数量是固定的
# 属性：
1.T	        数组转置
2.dtype	    元素类型
3.flat	    将ndarray转换为一维数组
4.size	    元素数量
5.itemsize  每个元素的内存容量，以byte为单位
6.nbytes	数组总共占据的内存大小，单位为byte
7.ndim	    维度数
8.shape	    数组形状，表示为元组

```

### ndarray的创建

```python
#1.array()：从list, tuple对象中创建
np.array(object, dtype=None, ndmin=0)
object — list或tuple对象。强制参数。
dtype — 数据类型。可选参数。
ndmin — 最小维数。可选参数。

#2.asarray()：根据现有数组创建ndarray
numpy.asarray(a, dtype = None)

#3.fromstring()：从字符串中读取数据，并将其转换为一维数组。
np.fromstring(string, dtype=float, count=-1, sep=”)
string — 包含数据的字符串。强制参数。
dtype — 数据类型，默认为浮点型。可选参数。
count — 从左到右读取数据的个数。默认为-1，表示读取所有数据。可选参数。
sep — 分隔符。

#4.ones()：创建全1数组
np.ones(shape, dtype=None)
shape — 维度。强制参数。
dtype — 数据类型。默认为np.float64。可选参数。

#5.ones_like()：创建与参数数组形状和类型相同的ndarray，并将数组中所有元素填充为1。
np.ones_like(a, dtype=None)
a — 给定的数组。其维度和数据类型决定着要创建的数组的属性。强制参数。
dtype — 数据类型。默认的“None”意为“a.dtype”。可选参数。

#6.zeros()：创建全0数组
np.zeros(shape, dtype=float,)
shape — 维度。强制参数。
dtype — 数据类型。默认为np.float64。可选参数。


#7.zeros_like()：创建与参数数组形状和类型相同的ndarray，并将数组中所有元素填充为0。
np.zeros_like(a, dtype=None)
a — 给定的数组。其维度和数据类型决定着要创建的数组的属性。强制参数。
dtype — 数据类型。默认的“None”意为“a.dtype”。可选参数。


#8.empty()：返回一个没有初始化内存的数组，创建出来的全空数组中的数据都是无限小的、无限接近于0但不是0。
np.empty(shape, dtype=float)
shape — 维度。强制参数。
dtype — 数据类型。默认为np.float64。可选参数。


#9.empty_like()：返回一个与给定数组的维度和数据类型相同的新数组。
np.empty_like(a, dtype=None)
a — 给定的数组。其维度和数据类型决定着要创建的数组的属性。强制参数。
dtype — 数据类型。默认的“None”意为“a.dtype”。可选参数。


#10.full()：返回一个指定维度和数据类型的新数组，并用指定的值填充
np.full(shape, fill_value, dtype=Non)
shape — 维度。强制参数。
fill_value — 填充值。强制参数。
dtype — 数据类型。默认的“None”意为“np.array(fill_value).dtype”。可选参数。


#11.full_like()：返回一个与给定数组的维度和数据类型相同的新填充数组。
np.full_like(a, fill_value, dtype=None)
a — 给定的数组。其维度和数据类型决定着要创建的数组的属性。强制参数。
fill_value — 填充值。强制参数。
dtype — 数据类型。默认的“None”意为“np.array(fill_value).dtype”。可选参数。


#12.eye()：创建对角矩阵,返回一个矩阵（即二维数组），其对角线上均为1，其余位置均为0。
eye(N, M=None, k=0, dtype)
N — 行数。强制参数。
M — 列数。默认值为None，意为“同N”。可选参数。
k — 对角线索引。k=0，指主对角线；k为正整数，指从第k个值开始的右上对角线；k为负整数，指从第-k个值开始的左下对角线。可选参数。
dtype — 数据类型。默认为浮点数。可选参数。


#13.identity()：创建单位矩阵，即主对角线上为1而其余位置为0的方阵。
identity(n, dtype=None)
n — 行数和列数。即生成的是nxn的方阵。强制参数。
dtype — 数据类型。默认为浮点数。可选参数。

#14.copy()：深拷贝
copy(a)
a — 已知数组。强制参数。


#15.reshape()：改变数组的形状。通过reshape生成的新数组和原始数组共用一个内存，也就是说，若更改其中数组的元素，另一个数组也将发生改变。
reshape(a, newshape)
a — 已知数组。强制参数。
newshape — 新的维度，为整数或由整数组成的元组。强制参数。


#16.创建等差数列数组 - arange()
np.arange(start, stop, step, dtype=None)
start — 起始值（取得到）。默认值为0。可选参数。
stop — 终止值（取不到）。强制参数。
step — 步长。默认值为1。若指定step，则start值必须给出。可选参数。
dtype — 数据类型。若不指定数据类型，则通过其他参数（如start, stop, step）判断。可选参数。


#17.linspace() - 创建一个一维数组，在给定的区间上num等分。
np.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None)
start — 区间起始值。强制参数。
stop — 区间终止值（是否取得到，需要设定参数endpoint）。强制参数。
num — 等分的个数。默认值为50。可选参数。
endpoint — 若为True（默认），则可以取到区间终止值；否则取不到。可选参数。
retstep — 若为True，则返回由生成的数组和步长构成的元组；若为False（默认），则只返回生成的数组。可选参数。
dtype — 数据类型。若不指定数据类型，则通过其他参数判断。可选参数。


#18.rand() - 随机数组
1.np.random.randint(low,high,size)
low:起始值
high：终止值（不包括）
size：等同于shape
2.np.random.rand(row,col)创建一个给定类型的数组，将其填充在一个均匀分布的随机样本[0, 1)。
```

### 索引

```python
#1.布尔索引
print(arr[arr > 25])  # 取出大于 25 的元素 -> [30 40 50]
#2.花式索引
idx = [0, 3, 4]  # 选索引 0, 3, 4
print(arr[idx])  # -> [10 40 50]

arr2d = np.array([[1, 2, 3], 
                  [4, 5, 6], 
                  [7, 8, 9]])
rows = [0, 1, 2]  # 选 3 行
cols = [2, 1, 0]  # 选 3 列
print(arr2d[rows, cols])  # -> [3 5 7] 选择索引为(0,2),(1,1),(2,0)的元素

```

### 广播

```python
#广播是指 NumPy 在算术运算期间处理不同形状的数组的能力
#广播的规则
#1.所有输入数组都向形状最长的数组对齐，较小的数组会在前面追加一个长度为 1 的维度。
有两个输入数组的形状分别为(3,1),(3,)
(3,)->(1,3)
#2.输出数组的形状是输入数组各个维度上的最大值
有两个输入数组的形状分别为(3,1),(1,3)
输出数组形状为(3,3)
#3.如果输入数组的某个维度和输出数组的对应维度相同或者为1，或其值正好为 1，则该数组可以用来计算
```

### 数组迭代

```python
print  '以 C(行优先) 风格顺序迭代：'  
for x in np.nditer(a, order =  'C'):  
    print x,  
print  '以 F(列优先) 风格顺序迭代：'  
for x in np.nditer(a, order =  'F'):  
    print x,
```

### 数组操作大全

#### 修改数组形状

```python
#1.修改数组形状
reshape(newshape) 
-newshape：新的形状应当兼容原有形状

#2.该函数返回数组上的一维迭代器
ndarray.flat

#3.该函数返回折叠为一维的数组副本      
ndarray.flatten()

```

#### 数组反转

```python
#1.数组转置
ndarray.T
#2.数组转置
numpy.transpose(arr, axes=())
-arr：要转置的数组
-axes：维度，通常所有维度都会翻转
numpy.transpose(arr,axes=(1,0))
```

#### 数组连接

```python
#1.沿指定轴连接相同形状的两个或多个数组
numpy.concatenate((a1, a2, ...), axis)
-a1, a2, ...：相同类型的数组序列
-axis：沿着它连接数组的轴，默认为 0
 
第一个数组：
[[1 2]
 [3 4]]
 
第二个数组：
[[5 6]
 [7 8]]
 
沿轴 0 连接两个数组：
[[1 2]
 [3 4]
 [5 6]
 [7 8]]
 
沿轴 1 连接两个数组：
[[1 2 5 6]
 [3 4 7 8]]

#2.沿指定轴堆叠相同形状的两个或多个数组
numpy.stack((a1, a2, ...), axis)
-a1, a2, ...：相同类型的数组序列
-axis：返回数组中的轴，输入数组沿着它来堆叠
 
第一个数组：
[[1 2]
 [3 4]]
 
第二个数组：
[[5 6]
 [7 8]]
 
沿轴 0 堆叠两个数组：
[[[1 2]
 [3 4]]
 [[5 6]
 [7 8]]]
 
沿轴 1 堆叠两个数组：
[[[1 2][5 6]]
 [[3 4][7 8]]]
```

#### 数组分割

```python
numpy.split(ary, indices_or_sections, axis)
该函数沿特定的轴将数组分割为子数组。函数接受三个参数：
-ary：被分割的输入数组
-indices_or_sections：可以是整数，表明要从输入数组创建的，等大小的子数组的数量。 如果此参数是一维数组，则其元素表明要创建新子数组的点。
-axis：默认为 0

第一个数组：
arr=np.array([[1,2,3,4],
              [5,6,7,8]])

沿轴 0 分割两个数组：
np.split(arr,indices_or_sections=2,axis=0)

[array([[1, 2, 3, 4]]), array([[5, 6, 7, 8]])]

沿轴 1 分割两个数组：
np.split(arr,indices_or_sections=2,axis=1)

[array([[1, 2], [5, 6]]), array([[3, 4], [7, 8]])]
```

#### 添加/删除元素

```python
#1.输入数组的末尾添加值
1.numpy.append(arr, values, axis)
-arr：输入数组
-values：要向arr添加的值，比如和arr形状相同（除了要添加的轴）
-axis：沿着它完成操作的轴。如果没有提供，两个参数都会被展开

#2.此函数在给定索引之前，沿给定轴在输入数组中插入值
numpy.insert(arr, obj, values, axis)
-arr：输入数组
-obj：在其之前插入值的索引
-values：要插入的值
-axis：沿着它插入的轴，如果未提供，则输入数组会被展开

data_a=np.array([[1,2,3,4],[5,6,7,8]])
print(np.insert(data_a,0,[0,0],axis=1))
[[0 1 2 3 4]
 [0 5 6 7 8]]

#3.返回从输入数组中删除指定子数组的新数组
Numpy.delete(arr, obj, axis)
arr：输入数组
obj：可以被切片，整数或者整数数组，表明要从输入数组删除的子数组
axis：沿着它删除给定子数组的轴，如果未提供，则输入数组会被展开

#4.去重
numpy.unique(arr, return_index, return_inverse, return_counts)
-return_index：如果为true，返回输入数组中的元素下标
-return_inverse：如果为true，返回去重数组的下标，它可以用于重构输入数组
-return_counts：如果为true，返回去重数组中的元素在原数组中的出现次数
```

#### 位操作

```python
1.	Numpy.bitwise_and(a,b) 对数组元素执行位与操作
2.	Numpy.bitwise_or(a,b) 对数组元素执行位或操作
3.	Numpy.invert(a) 计算位非
4.	Numpy.left_shift(a,width) 向左移动width位
5.	Numpy.right_shift(a,width) 向右width位
```

#### 算术函数

##### 三角函数

```python
1.通过乘 pi/180 将角度转化为弧度  
np.sin(a*np.pi/180)
```

##### 舍入函数

```python
1.numpy.around(a,decimals)：四舍五入
-a 输入的数或数组
-decimals 要舍入的小数位数。 默认值为0。 如果为负，整数将四舍五入到小数点左侧的位置
2.numpy.floor()：向下取整
3.numpy.ceil()：向上取整
```

##### 算术函数

```python
1.numpy.reciprocal(a)：求倒数
-a:数或数组
2.numpy.power(a,n)：求n次幂
-a:数或数组
-n:幂
```

#### 统计函数

```python
1.numpy.mean(a,axis):按轴返回数组算数平均值
-a：数组
-axis：轴，如果没有提供，数组都会被展开成一维数组
2.numpy.average(a,weight,axis):按轴求加权平均值
数组[1,2,3,4]和相应的权重[4,3,2,1]
加权平均值 = (1*4+2*3+3*2+4*1)/(4+3+2+1)
-a：数组
-weight：权重
-axis：轴，如果没有提供，数组都会被展开成一维数组
```

#### 排序函数

```python
1.numpy.sort(a, axis, kind)
-a：要排序的数组
-axis：沿着它排序数组的轴，如果没有数组会被展开，沿着最后的轴排序
-kind：默认为'quicksort'（快速排序）.'quicksort'（快速排序）,'mergesort'（归并排序）	'heapsort'（堆排序）

2.numpy.argsort()：返回数据的索引数组,这个索引数组用于构造排序后的数组。
-a：要排序的数组
-axis：沿着它排序数组的轴，如果没有数组会被展开，沿着最后的轴排序
-kind：默认为'quicksort'（快速排序）.'quicksort'（快速排序）,'mergesort'（归并排序）	'heapsort'（堆排序）
```

#### 查找函数

```python
1.numpy.amin(a,axis)和numpy.amax(a,axis):按轴返回数组最小值最大值
-a：数组
-axis：轴，如果没有提供，数组都会被展开成一维数组
2.numpy.argmax(a,axis) 和 numpy.argmin(a,axis)：这两个函数分别沿给定轴返回最大和最小元素的索引。
-a：数组
-axis：轴，如果没有提供，数组都会被展开成一维数组
3.numpy.nonzero(a)：函数返回输入数组中非零元素的索引。
-a：数组
4.numpy.where(condition)：函数返回输入数组中满足给定条件的元素的索引。
-condition：条件
y = np.where(x >  3) 
5.numpy.extract(condition，array)函数返回输入数组中满足给定条件的元素
-condition：条件
-array：数组
np.extract(data%2==0,data)
```

#### 副本与视图

```python
1.视图：
在NumPy中，视图是对原始数据的另一种展示方式，它并不复制数据，而是提供原始数据的不同访问方式。视图和原始数据共享相同的内存空间。这意味着对视图所做的任何修改都会反映到原始数据上，反之亦然。创建视图的方法之一是使用切片操作。
+ numpy 的切片操作返回原数据的视图
+ 调用 ndarray 的 view() 函数产生一个视图
+ ndarrat.T
+ nummpy.transpose

2.副本：
与视图不同，副本是原始数据的完整复制。这意味着副本和原始数据占用不同的内存空间，对副本的修改不会影响原始数据，反之亦然。在NumPy中，可以使用copy()方法或np.copy()函数来创建副本。
```

#### 线性代数

```python
1.numpy.dot(arr1,arr2)：二维向量，其等效于矩阵乘法。 对于一维数组，它是向量的内积
2.numpy.vdot(arr1,arr2)：返回两个向量的点积。 如果第一个参数是复数，那么它的共轭复数会用于计算。 如果参数是多维数组，它会被展开
3.numpy.inner(arr1,arr2):返回一维数组的向量内积。
4.numpy.matmul(arr1,arr2):返回两个数组的矩阵乘积
5.numpy.linalg.det(arr):返回行列式的值
6.numpy.linalg.inv(arr)：求可逆矩阵
7.numpy.linalg.solve(arr)：求线性方程的解。
```
