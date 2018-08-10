---
title: cplex的使用环境
date: 2018-08-09 17:01:47
tags:
  - anaconda
  - theano
  - keras
  - cplex
categories:
  - 环境搭建
---
最近的一个实验中用到了cplex和keras，现有的支持只有cplex的win版本，并且只支持python2的32位版本，所以在这里记录一下环境搭建过程。

# CPLEX
CPLEX是IBM发布的一款软件，提供了用来求解线性规划（LP）等相关问题的函数库，并且支持Python、Matlab等多种语言的调用，详细介绍可以参考IBM的官方介绍文档。

试过pip install cplex和conda install -c IBMDecisionOptimization docplex cplex这两种，import cplex没有问题，但是跑实验时会报错求解问题size超过限制。
有安装可执行文件，所以双击正常安装，需要java环境，按照提示操作就可以，安装完成后的界面和eclipse相似。

# Anaconda
python选择通过anaconda来安装，anaconda包含了Python、Conda等一系列的工具包，使用起来很方便。
[官网](https://www.anaconda.com/download/)下载安装包，正常安装

# theano
因为tensorflow在windows下不支持python2，所以用theano做keras的后端
## 安装MinGW
试过CodeBlock内置的MinGW和单独下载安装MinGW，都不行，会报编译错误，只能通过conda来安装了，安装之前一定要换源
``` python
conda install mingw libpython
```
下载安装完成后，要在Path中添加环境变量
D:\(anaconda的安装目录)\MinGW\bin
D:\(anaconda的安装目录)\MinGW\i686-w64-mingw32(依平台而定)\lib
并且注意，Path中只能有这一个MniGw变量。
## 下载
``` python
pip install theano
```
添加PYTHONPATH环境变量
D:\(anaconda的安装目录)\Lib\site-packages\theano
## 配置文件
在C:\Users\(用户名)目录下新建.theanorc.txt文件，添加内容入下：
``` python
[blas]
ldflags=

[gcc]
cxxflags=-ID:\(anaconda的安装目录)\MinGW\i686-w64-mingw32\include
```
# keras
安装之前一定要换源
``` python
pip install keras
```
因为keras默认后端是tensorflow，所以要修改位theano
修改后端文件，在C:\Users\(用户名)\.keras\keras.json中，把tensorflow改成theano

# python调用cplex
在D:\(cplex的安装目录)\cplex\python\x86_win32目录下运行setup.py文件
``` python
python setup.py install
```
生成build文件夹
在环境变量PYTHONPATH中添加D:\(cplex的安装目录)\cplex\python\x86_win32

这样应该就可以用了。
