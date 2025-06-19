# npm

## 配置镜像源

```js
//获取当前镜像源
npm config get registry
//设置镜像源
npm config set registry https://registry.npmmirror.com
```

## 安装软件包

```js
npm install [可选参数] <package_name>@版本号
g：全局安装
--save：     在package文件的dependencies写入依赖
--save-dev:  在package文件的devDependencies写入依赖
```

## 卸载软件包

```js
npm uninstall [可选参数] <package-name>
g：删除全局安装
--save：     
--save-dev
```

## 更新软件包

```
npm update <package_name>
```

## package.json

```
name 设置了应用程序/软件包的名称。
version 表明了当前的版本。
description 是应用程序/软件包的简短描述。
main 设置了应用程序的入口点。
private 如果设置为 true，则可以防止应用程序/软件包被意外地发布到 npm。
scripts 定义了一组可以运行的 node 脚本。
dependencies 设置了作为依赖安装的 npm 软件包的列表。
devDependencies 设置了作为开发依赖安装的 npm 软件包的列表。
engines 设置了此软件包/应用程序在哪个版本的 Node.js 上运行。
browserslist 用于告知要支持哪些浏览器（及其版本）
```









