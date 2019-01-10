---
title: OpenCasCade 安装笔记
date: 2018-04-27 10:02:46
tags: 笔记
---
## 环境安装
### 1.配置基本库：
 安装常用的开发编译工具包：
 ```bash
 sudo apt-get install build-essential 
 sudo apt-get install automake autoconf 
 ```
 配置OpenGL库：
 ```bash
 sudo apt-get install freeglut3-dev 
 ```
 
### 2.配置第三方库（3rd-Party Libraries)
 必需的库：Tcl/Tk, FreeType
 可选库：TBB 3.x-4.x, gl2ps 1.3.5-1.3.8, FreeImage 3.14.1-3.15.4
 命令：
 ```bash
 sudo apt-get install tcllib tklib tcl-dev tk-dev     
 ```
 去下载Freestyle源码,解压后在目录打开终端，命令：
 ```bash
 ./configure
 make
 sudo make install  #这是一般编译第三方库通用的素质三连
 ```
 
### 3.编译Opencascade库
 首先你需要先下载库（这里是opencascade-7.2.0.tgz [百度网盘](https://yun.baidu.com/pcloud/album/info?uk=3808749571&album_id=1612598197766366243)）
 解压到合适文件夹，打开终端，命令：
 ```bash
 mkdir build
 cd build
 cmake ../    #需要安装cmake
 make         #耐心地等待（估计1h的时间）
 sudo make install
 ```
 Tips:
 为防止make语句执行到41%处报错无法找到“-lXmu"和”-lXi"，需要在终端进入/usr/lib/x86_64-linux-gnu目录，执行以下代码：
 ```bash
 sudo ln -s libXmu.so.6 libXmu.so
 sudo ln -s libXi.so.6 libXi.so
 ```
 报错原因为在对应目录下找不到libXmu.so和libXi.so文件，其实这些文件存在只是默认命名加上了版本号（如“libXmu.6.1.0”,之前代码中给出的.6也是一个链接），我们在对应目录下生成指向文件的软链接（类似快捷方式）就可以解决报错。
 
## 测试
 至此环境安装结束，测试过程如发现文件权限问题导致打不开可以用chmod命令修改文件权限。
### 打开igs文件
 在build目录下打开终端，输入命令：
```bash
./draw.sh
pload ALL
igesread file.igs igs
1
3
0
vdisplay Shape_1
vfit             #将模型居中
vsetdispmode 1   #默认为0只显示网格，1为显示模型材质<<实践经验
```
## 参考网址：
 https://www.cnblogs.com/opencascade/p/4003308.html
 http://www.cppblog.com/eryar/archive/2014/09/25/208421.html（网格）
