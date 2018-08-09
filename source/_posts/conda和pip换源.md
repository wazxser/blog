---
title: conda和pip换源
date: 2018-08-09 17:17:12
tags:
  - conda
  - pip
categories:
  - 环境搭建
---
推荐使用国内镜像下载

# pip
## 国内源
清华大学：https://pypi.tuna.tsinghua.edu.cn/simple
阿里云：http://mirrors.aliyun.com/pypi/simple/
豆瓣：http://pypi.doubanio.com/simple/
中科大：https://mirrors.ustc.edu.cn/pypi/web/simple/

## 更换源
以更换清华的源为例：
### 临时使用
使用-i参数，加上下载地址
示例：
``` python
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple keras
```

### 永久使用
#### Linux
在~/.pip/pip.conf文件中加入如下内容，没有则创建该文件
#### Windows
找到用户目录下的AppData文件夹（显示隐藏项目或者资源管理器中直接搜索%appdata%），进入Local创建pip文件夹，创建pip.ini文件，添加如下内容
``` python
[global]
timeout = 6000
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
trusted-host = pypi.tuna.tsinghua.edu.cn
```

# conda
## 国内源
conda国内的源貌似只有清华的：https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
## 更换源
### 换源命令
``` python
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --set show_channel_urls yes
```
### 换回默认源
``` python
conda config --remove-key channels
```
