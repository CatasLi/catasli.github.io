---
title: TensorFlow 安装笔记
date: 2018-05-05 11:53:47
tags: 笔记
---
## 环境

* Ubuntu16.04
* Python2.7.12

## 主要命令
```bash
$ sudo apt-get install python-pip python-dev
$ sudo pip install tensorflow #会自动安装依赖包
```
附上test.py测试用的代码：
```python
import tensorflow as tf

hello=tf.constant("Hello TensorFlow!")
sess=tf.Session()
print sess.run(hello)
```
附上Pycharm安装命令：
首先添加源
```bash
$ sudo add-apt-repository ppa:mystic-mirage/pycharm
```
然后根据需求安装正式版（收费需激活）或者社区版（免费）
```bash
$ sudo apt update
$ sudo apt install pycharm #社区版为pycharm-community
```
## Tips:
程序运行时可能会出现“Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2 FMA”类似的提示（I），意思为当前CPU支持AVX（Advanced Vector Extensions），运算速度还可以提升，所以可以开启更好更快的模式，但是你现在用的模式相对来说可能不是那么快，所以这个其实并不是存在错误，所以如果不嫌当前的模式慢就忽略掉这个警告就好了。 [参考网址](https://blog.csdn.net/CliuGeek/article/details/78836598)
强迫症解决方案：
在程序前加上：
```pyhton
import os
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2'
```
这样可以关闭提示。
