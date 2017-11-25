---
title: npm文档翻译(二)
date: 2017-11-23 15:23:05
tags: Npm
---

### 安装Node.js和升级npm

1. 安装Node.js
  如果你用OSX或者Windows系统,最好的安装Node.js的方式是从[Node.js Download page](https://nodejs.org/en/download/)安装,如果你用的是Linux系统,你也能用这个安装程序,或者你能从[NodeSource's binary distribution](https://github.com/nodesource/distributions) 看看是否有最近的能在你电脑上使用的版本.

  测试: 输入 node -v .显示的版本应该比v0.10.32更高

2. 升级npm
  随着Node安装了npm也会被安装,此时你应该有一个版本的npm.然而,npm比Node更新更频繁,所以如果你想确保npm是最新版本,用下面的命令:
  ```
  npm install npm@latest -g
  ```
  测试: 输入 npm -v . 显示的版本应该比2.1.8更高

3. 手动安装npm
为了更多的高级用户,npm模块可以在下面的地址下载
```
https://registry.npmjs.org/npm/-/npm-{VERSION}.tgz
```
