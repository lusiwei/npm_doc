---
title: npm文档翻译(三)
date: 2017-11-25 16:10:17
tags: Npm
---

### 修复npm权限
当你安装一个全局包的时候,你可能收到一个EACCES错误,这就暗示着你没有npm存放全局包和命令所在目录的写权限

你能够修复这个问题用下面三种方法之一:

  1. 改变npm默认目录的权限
  2. 把npm默认目录修改成另外一个目录
  3. 用包管理器去安装Node,让包管理器去负责权限问题

#### 1. 改变npm默认目录的权限
  * 1.找到npm目录的路径
    ```
    npm config get prefix
    ```
    许多系统的默认目录都是: **/usr/local**
    **警告**:如果显示的目录是 **/usr**,那么就用方法2,否则你将会弄乱你的权限
  * 2.改变npm目录的所有者为当前用户
     ```
       sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}
      ```
    这条命令改变了npm所使用的子文件夹的权限和一些其他的工具的权限(lib/node_modules,bin,and share).

#### 2. 把npm默认目录修改成另外一个目录
有些时候当你改变npm默认目录的所有者时可能会导致一些问题,例如你和其他用户共享这个操作系统的时候.

可代替的方法是,你能够配置你的npm去使用一个完全不同的目录,在我们的例子中,这个目录将是home目录下面的一个隐藏的目录
  * 1.为全局安装创建一个目录
```
mkdir ~/.npm-global
```

  * 2.配置npm去使用这个新建的目录
```
npm config set prefix '~/.npm-global'
```

  * 3.打开或者创造一个 ~/.profile 文件然后添加下面这行
  ```
  export PATH=~/.npm-global/bin:$PATH
  ```

  * 4.回到命令行,更新你的系统变量
  ```
  source ~/.profile
  ```

测试:不使用sudo下载一个全局包
```
npm install -g jshint
```
代替第2到第4步,你能够用相应的环境变量(例如如果你不想修改~/.profile文件)
```
NPM_CONFIG_PREFIX=~/.npm-global
```

#### 3.用包管理器去安装Node,让包管理器去负责权限问题
如果你是做做一个全新的安装在Mac OS上,你将能够完全避免这个问题,通过用[Homebrew](http://brew.sh/)包管理器.Homebrew将会用正确的权限安装.
```
brew install node
```
