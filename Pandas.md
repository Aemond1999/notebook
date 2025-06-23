# Pandas

## Series

### 创建Series

```python
#series由两个部分组成：values(一维ndarray类型)，index(索引)
pandas.Series(arr，index=[])
-arr：数据容器/ndarray
-index：指定索引(可选)
```

### 索引

 ```python
 1.显式索引：loc[]
 使用index中的元素作为索引
 2.隐式索引：iloc[]
 用数组下标作为索引
 ```

### Series基本属性与方法

```python
1.Series.shape：返回形状
2.Series.dtypes：返回数据类型
3.Series.size：返回长度
4.Series.index.values：返回索引
5.Series.values：返回所有值
6.Series.head(n)：返回前n行数据，默认前5行数据
7.Series.tail(n)：返回后n行数据，默认后5行数据
8.Series.isnull()：查看空值
```

### Series运算机制

```python
1.运算中自动对齐索引
2.若索引对不齐则补NaN
3.Series没有广播机制
```

## DataFrame

### 创建DataFrame

```python
#DataFrame有三个部位组成：values(二维ndarray)，columns(列名)，index(行索引)
1.pandas.DataFrame(字典,index)
  -index：行索引
2.pandas.DataFrame(二维数组,index,columns)
  -index：行索引
  -columns：列索引
```

### DataFrame基本属性和方法

```python
1.DataFrame.shape：返回形状
2.DataFrame.info():打印数据表基本信息（维度、列名称、数据格式、所占空间）等
3.DataFrame.dtypes：返回数据类型
4.DataFrame['列名'].dtype：返回某列的数据类型
5.DataFrame.columns：返回每一列列名
6.DataFrame.values：返回所有值
7.DataFrame.head(n)：返回前n行数据，默认前5行数据
8.DataFrame.tail(n)：返回后n行数据，默认后5行数据
9.DataFrame['列名'].isnull()：查看某一列空值
10.DataFrame.value_counts()
11.DataFrame.describe()：统计每一列count,mean,std,25%,50%,75%,max,min
12.DataFrame.query('列名+条件'):查找满足条件的所有行
13.DataFrame.drop(labels,axis,inplace):删除Dataframe某行或某列的数据 
  -labels:接收一个列表，内含删除行 / 列的索引编号或索引名
  -axis:删除的轴向,默认为行，0代表删除行；1代表删除列
  -inplace:是否改变原数组,默认False 即生成一个新数组
14.df['列名'] = df['列名'].astype('int')
```

### 数据导入和导出

#### 数据导入

```python
1.pandas.read_excel(filename，sheet_name,index)：导入excel文件
  -filename：文件路径
  -sheet_name：工作表名(可选)
  -index:index为False表示不导入索引
2.pandas.read_csv(filename,sep,header,names=[],index)：导入csv，txt等用逗号，tab等分割的文本文件
  -sep：分隔符
  -header：有无列名，默认为第一行
  -names:若无列名，则指定列名
  -index:index为False表示不导入索引
3.pandas.read_sql(sql,conn,index):读入sql查询的数据
  -index:index为False表示不导入索引
  -sql:sql语句
  -conn：数据库连接
  步骤：
    1.import sqlalchemy 
    2.con=create_engine('mysql+pymysql://{用户名}:{域名}@{ip地址}/{数据库名}')
```

#### 数据导出

```python
1.df.to_csv(filename, index)
  -index：index=False 表示不导出 DataFrame 的索引,index默认为True
2.df.to_excel(filename, sheet_name, index)
3.df.to_sql(表名, conn, if_exists, index)
  -if_exists 参数可以是 'fail'（如果表存在则引发错误）、'replace'（替换表）、'append'（在表中添加数据）
```

### 缺失值处理

```python
#1.判断是否有缺失值
   np.any(df.isnull())
   np.all(df.notnull())
#2.过滤缺失值
   1.cond=np.all(df.notnull(), axis=1)
   2.print(df[cond])
#3.删除缺失值所在行/列
   DataFrame.dropna(axis, how, thresh, subset, inplace):删除缺失值所在的行/列
   -axis:0代表删除包含缺失值的行,1代表删除包含缺失值的列,默认为行
   -how:'any'代表删除有缺失值的行/列;'all'代表删除所有值均缺失的行/列
   -thresh:指定非 Na 值的数量，非 Na 数量大于等于 thresh 时不删除
   -subset:输入一个含索引名称的list，代表对这些列的空值进行删除
   -inplace:是否改变原数组,默认False 即生成一个新数组
#4.填充缺失值
  DataFrame.fillna(value, method, axis, inplace):填充缺失值
  -value：填充的值，也可输入一个字典（用于为不同的列设置不同的填充值）
  -method：填充方法,“ffill”用前一行/列的值填充，“bfill”用后一行/列值填充,与axis搭配使用
  -axis：修改填充的轴,axis=0代表行,axis=1代表列
```

### 聚合函数

```python
# df.聚合函数(axis=None, skipna=None)
  -axis:0 表示按列，1 表示按行
  -skipna:是否忽略 NaN，True 表示不计算 NaN，默认为 True
1.sum()
2.min()
3.max()
4.median()
5.std()：标准差
6.var()：方差
7.count():返回所有元素的总数
8.groupby(labels,axis)
9.DataFrame.sort_values(列名):根据值排序
10.DataFrame.sort_index():根据索引排序
11.df.agg({"列名":聚合函数})
```

### 删除重复值

```python
1.DataFrame.drop_duplicates(subset, keep, inplace): 删除重复值所在行
  -subset：输入一个list，用来要操作的列，默认是所有列
  -keep：指定处理重复值的方法：“first” 指保留第一次出现的值，“last” 指保留最后一次出现的值
        “False” 不保留重复值，全部删除\
    
2.DataFrame.replace(被替换的元素，替换元素):元素替换
  注意：如果要一次替换多个不同的值，可以利用列表或者字典；如果想仅对某列替换，先利用df[]切片即可
```

### 数据映射

```python
1.map()：处理单独的列
  它非常适合处理某一列数据的映射操作。可以通过传入 lambda 表达式或自定义函数，对列数据进行批量转换。
    
2.apply(fun,axis)：处理 Series 和 DataFrame
  apply()它不仅可以应用于 Series，还可以应用于 DataFrame。apply() 可以处理数据框中的每一列或每一行
    
3.transform([funs],axis=0)：主要用于对每行/列进行多个运算。与 apply() 相比，transform() 可以同时返回多个变换结果，并且保持原数据的形状。
```

### 表合并

```python
1.pandas.merge(df1,df2,...):左右合并，拼接的依据为列索引
  -on:指定合并时依据的列名，,on默认的是相同列名，两个表的列名不同时不能使用
  -how:表示连接方式，inner(默认),outer,left,right
  -suffixes:参数指定当两个表合并后有相同的列名时，在列名上加的前缀，默认为元组（'_x','_y'）
  -left_on:左表用于连接的列名,两个表的列名不同却要根据这两个列名下的属性值来合并的时候使用
  -right_on:右表用于连接的列名
  -sort：默认为False，将合并的数据进行排序
  
2.df.join(df1,...):左右合并，拼接的依据为行索引
  上述参数中除了how的默认值为“left”外其他的都和merge相同
   
3.pandas.concat(objs=[], axis=0, join='outer',ignore_index=False)
  -axis:上下拼接，依据是列名 axis=0,左右拼接，依据是index,axis=1
  -ignore_index：重建索引，默认为False

4.df.append.(to_append, ignore_index=False)：上下拼接，合并依据为列名
  -to_append:要追加的df
```

### 数据分箱

```python
  #1.等距分箱
    pd.cut(df.列名,bin,right)
    -bins：分几个箱，可自定义分箱
    -lables:给分箱命名
    -right：默认为True，左开右闭区间
  #2.等频分箱
    pd.qcut(df.列名,bin,right)
```

### 时间序列

#### TimeStamp

 ```python
 #1.创建时间戳
 pd.Timestamp("时间")
 #2.批量创建时间戳
 pd.data_range(start,end,period,freq)->DatetimeIndex
 -period:生成几个时间戳
 -start：开始时间
 -end：结束时间
 -freq：时间频率
 #3.转化为时间戳
 pd.to_datetime(arg, errors='raise', format=None)
 -arg: 要转换的日期、时间、字符串或类似对象。
 -errors: 指定在转换失败时的处理方式，可以是 ‘raise’（默认，抛出异常）、‘coerce’（将无法转换的值设为 NaT）或 ‘ignore’（忽略错误）。
 -format: 指定日期字符串的格式
 ```

#### Period

```
#1.创建时间段
pd.Period("时间",freq)
#2.批量创建时间段
pi = pd.period_range(start,end,period,freq)
```

#### 重采样

```python
ts.resample('2D',on).sum(): 按两天进行汇总，D:天,W:星期,M：月,H：小时,T：分钟
-on：指定列名进行采样，默认为行索引
```

#### 时区

```py
import pytz
ts.tz_convert(时区):转换时区
```



