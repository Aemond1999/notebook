# Git

## 初始设置

```sh
#1.设置用户名和邮箱
git config --global user.name= '用户名'
git config --glbobal user.email='邮箱'
或者直接在.gitconfig文件中修改
#2.生成ssh
ssh-keygen -t rsa -C "注册github的邮箱"
```

## 基本操作

```sh
#1.初始化仓库
git init 
#2.查看仓库状态
git status
#3.将文件添加到暂存区
git add 文件名
#4.将工作区所有文件添加到暂存区
git add .
#4.将暂存区所有文件提交到仓库中
git commit -m '描述本次提交' 
#5.将暂存某一文件提交到仓库中
git commit -m '描述本次提交' 文件名 
#6.查看以当前日志
git log
#7.只显示与某一日志有关的日志
git log 文件名
#8.查看当前工作区与暂存区的差别
git diff
#9.查看当前工作区与暂存区与最新提交之间的差别
git diff HEAD
#10.图表形式显示日志
git log --graph
#11.查看全局日志
git reflog
```

## 分支操作

```sh
#1.显示所有分支
git branch
#2.创建分支，分值实际上是master的复制，继承master分支的所有资源
git branch 分支名
#3.切换分支
git checkout 分支名
#4.会到上一个分支
git checkout -
#5.合并分支
git merge --no-ff 分支名
#6.版本回溯
git reset --hard 版本号
#7.解决冲突
用编辑器打开冲突文件修改成想要的内容，然后 git add ,git commit
#8.修改分支名
git branch -m 分支名 新的分支名
```

## 修改已提交文件中的错误

```sh
#第一步
修改工作区文件，然后提交至仓库
#第二步
git rebase -i HEAD~2(打开最新提交前两条历史),将修改操作前面的pick 改为 fixup
```

## 暂存工作区

```sh
#1.备份当前的工作区的内容，从最近的一次提交中读取相关内容，让工作区保证和上次提交的内容一致。同时，将当前的工作区内容保存到Git栈中。
git stash 
#2.查看暂存的列表
git stash list
#3.应用暂存的更改，开发者可以使用 git stash apply 命令将 stash 中的更改应用到当前工作区。如果不指定 stash 名称，则会默认应用最新的 stash（stash@{0}），或者，开发者可以指定一个特定的 stash 名称来应用更改
git stash apply
git stash apply stash@{2}
#4.暂存的更改（并删除暂存）
git stash pop
git stash pop stash@{2}
#5.删除暂存记录
git stash drop stash@{2}
#6.清除所有暂存
git stash clear
```

## github远程仓库

### 基础操作

```sh
#1.添加远程仓库，远程仓库设置远程仓库名字为origin
git remote add origin git@github.com:用户名/仓库名.git
#2.获取远程分支
git branch 分支名 origin/远程分支名

```

### git clone

```sh
#.克隆，若不指定分支，默认克隆master
git clone -b 分支名 git@github.com:用户名/仓库名.git
```

### git push

```sh
#1.将本地分支与远程分支关联起来这样在以后使用 git push 时可以省略远程仓库和分支的名称
git push -u origin 远程分支名
#2.推送所有本地分支到远程仓库
git push --all origin
#3.删除远程仓库
git push origin --delete branch-name
```

### git fetch

```sh
#1.获取所有远程分支的更新
git fetch
#2.拉取指定分支的最新内容
git fetch 分支名
```

git pull

``` 
#获取所有分支的合并到本地分支上
git pull origin 远程分支
```













