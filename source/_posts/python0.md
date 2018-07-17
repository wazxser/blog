---
title: python的几个内置函数
date: 2018-01-29 21:55:24
tags: python
categories: 编程语言
---
Python is beautiful. (本文python环境为2.7.12)

# lambda表达式

## 语法
``` python
lambda (参数) : (计算表达式)
```

## 描述
目前知道的，lambda表达式在c#、java8、python都支持，主要作用为定义了一个匿名函数，使代码更加简洁

# map函数

## 语法
``` python
map(function, iterable, ...)
```

## 参数
* function: 函数
* iterable: 一个或多个列表
* python2返回列表
* python3返回迭代器

## 描述
map函数将列表元素依次传入函数，作为函数的参数值进行计算，返回计算结果，一般也为列表

## 示例
``` python
#python2.7
print(map(lambda x, y : x+y, [1, 2, 3], [2, 3, 4]))  #打印[3, 5, 7]
```

# reduce函数

## 语法

``` python
reduce(function, iterable[, initializer])
```

## 参数
* function: 函数，有两个参数
* iterable: 可迭代对象，例如，list
* initializer: 可选，初始参数
* 返回函数计算结果

## 描述
若无初始参数，reduce函数将可迭代对象的第1、2个之传入函数中进行计算，之后将计算结果与第3个值传入函数中，依次递推

若有初始参数，则第一步将初始参数和可迭代对象中第1个值传入参数中

## 示例
``` python
def add(x, y):
  return x+y

print(reduce(add, [1, 2, 3]))  #打印6

print(reduce(lambda x, y: x+y, [1, 2, 3]))  #打印6

print(reduce(lambda x, y : x+y, [1, 2, 3], 100))  #打印106
```
# zip函数

## 语法
``` python
zip([iterable, ...])
```

## 参数
* iterable: 一个或多个迭代器

## 描述
zip函数，可用于将迭代器中对应元素打包成元组，返回元组列表，若迭代器元素个数不一致时，以最少的元素个数为准。
此外，zip函数传入*操作符，可将元组解压

## 示例
``` python
list1 = [1, 2, 3]
list2 = [4, 5, 6]
list3 = [7, 8]

zipped = zip(list1, list2)
print(zipped)  #打印[(1, 4), (2, 5), (3, 6)]
print(zip(list1, list3)) #打印[(1, 7), (2, 8)]
print(zip(*zipped))  #打印[(1, 2, 3), (4, 5, 6)]
```
