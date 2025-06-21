# Conda

## 设置镜像源

```sh
#1.查看镜像源
conda config --show-sources
#2.删除一个镜像源
conda config --remove channels https://pypi.tuna.tsinghua.edu.cn/simple
#3.新增镜像源
 conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
 conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge
 conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
```

## 创建虚拟环境

```sh
#1.创建虚拟环境
conda create -n 环境名 python=3.8
#1.创建虚拟环境时指定路径（临时生效）
conda create --prefix=D:\conda_envs\环境名 python=3.9
#2.查看所有虚拟环境
conda env list
#3.激活虚拟环境
conda activate 环境名
#4.删除虚拟环境
conda remove --name 环境名 --all
#5.删除虚拟环境中的某个或者某些包
conda remove --name 环境名  包名
#导出环境中的所有配置
conda env export --name myenv > myenv.yml
#重新还原环境
conda env create -f  myenv.yml
```

## 包管理

```sh
#1.查询看当前环境中安装了哪些包
conda list
#2.查询是否有安装某个包
conda list package_name
#3.安装包
conda install package_name
#4.更新包
conda update package_name
#5.卸载包
conda uninstall package_name
```





