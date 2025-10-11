# networkX

## 创建图

```py
G1 = nx.Graph()    空的 无向图
G2 = nx.DiGraph()  空的 有向图
```

## 添加节点

```py
G.add_node('A')
G.add_node("A", label='A', color='red') 		添加带属性的节点
G.add_nodes_from(["A","B"])  							添加多个节点
G.add_nodes_from([("A", {"color": "red"})]) 添加多个节点以及属性
# 获取所有节点
nodes = G.nodes()
# 获取节点的属性
attributes = G.nodes[5]
```

## 添加边

```py
#添加边
G.add_edge(1, 2)
G.add_edge(2, 3, weight=4.2) 添加带权重的边
G.add_edges_from([(3, 4), (4, 5)]) 添加多条边
G.add_edge(1, 3, color='blue', weight=1.5) 添加带属性的边
# 获取所有边
edges = G.edges()
# 获取边的属性
edge_attrs = G[1][3]
```

## 查找节点或边

```py
# 获取节点的度数（节点连接的边数）
degree = G.degree(1)
# 检查节点是否存在
exists = G.has_node(1)
# 检查边是否存在
exists = G.has_edge(1, 2)
# 获取某个节点的邻居节点
neighbors = list(G.neighbors(1))
```

## 移除节点或边

```py
# 移除节点
G.remove_node(5)
# 移除多个节点
G.remove_nodes_from([3, 4])
# 移除边
G.remove_edge(1, 2)
# 移除多条边
G.remove_edges_from([(2, 3), (3, 4)])
```

## 为节点和边设置属性

```py
# 设置节点属性
G.nodes[1]['color'] = 'red'

# 设置边属性
G[1][2]['weight'] = 4.5
```

## 获取节点和边属性

```py
# 获取节点的颜色属性
color = G.nodes[1].get('color', 'blue')  # 如果不存在属性，则返回默认值 'blue'

# 获取边的权重属性
weight = G[1][2].get('weight', 1.0)

```

## 显示图像

```
nx.draw_networkx()
1.G:图像(必选)
2.pos
3.with_labels
4.node_color='skyblue'
5.node_size=1500
6.font_size=12
```

## 导出图

```py
# 导出为GraphML格式
nx.write_graphml(G, 'my_graph.graphml')

# 导出为GML格式
nx.write_gml(G, 'my_graph.gml')

# 导出为邻接表格式
nx.write_adjlist(G, 'my_graph.adjlist')

```

## 导入图

```py
# 从GraphML文件导入图
G = nx.read_graphml('my_graph.graphml')

# 从GML文件导入图
G = nx.read_gml('my_graph.gml')

# 从邻接表文件导入图
G = nx.read_adjlist('my_graph.adjlist')

```

