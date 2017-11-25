---
title: npm文档翻译(四)
date: 2017-11-25 17:13:31
tags:
---
### 局部安装npm包

有两种方法安装npm包:局部和全局,你选择哪种方式取决于你想怎样去用这个包

如果你想要在你自己的模块中去依赖一些包,例如请求Node.js包,然后你想要局部安装(npm install的默认安装行为),另一方面如果你想用它作为命令行工具,像grunt命令行界面,如果你想全局安装,请看下篇.
了解更多关于命令行安装的行为,请转到[CLI doc page](https://docs.npmjs.com/cli/install)

#### 安装
一个包能够被命令行下载通过下面这条命令
```
npm install <package_name>
```
这条命令将会在你当前目录创建node_modules目录(如果还不存在这个目录)，然后下载这个包到这个目录．

测试：
为了去确认npm install正常工作，去检查node_modules目录是否存在包含你所安装包的目录.　你能够运行**ls node_modules**命令在Unix操作系统上，例如"osx","Debian"等，或者在Windows上运行**dir node_modules**命令

例子：
安装一个叫做lodash的包．确认它是否成功安装通过列出node_modules目录的内容看是否有一个叫做lodash的目录

```
>npm install lodash
>ls node_modules   #use 'dir' for Windows

#=>lodash
```
#### 包的哪一个版本被安装了呢？
如果没有package.json文件在你的本地目录,这个最新的版本被安装了．
如果有package.json文件，这个最新版本在packages.json中满足semver rule的声明，那么这个包就被安装了

####　使用被安装的包
一旦这个包在node_modules里面，你就能在你的代码中使用．如果你创建了一个Node.js模块,你能够去请求这个包
例子:
用下面代码创建了一个index.js的文件
```
//index.js
var lodash=require('lodash');

var output=lodash.without([1,2,3],1);
console.log(output);

```
用node index.js运行这段代码,结果应该是output [2,3].
如果你没有正确的安装lodash,你将会收到以下报错:
```
module.js:340
    throw err;
          ^
Error: Cannot find module 'lodash'
```
修复这个问题,在与index.js相同的目录里运行npm install lodash
