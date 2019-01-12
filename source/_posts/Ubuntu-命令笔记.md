---
title: Ubuntu 命令笔记
date: 2019-01-10 21:58:43
tags: 笔记
---
安装deb
```bash
sudo dpkg -i package.deb
```
卸载软件
```bash
sudo dpkg -r software-name
```
编译源代码三连
```bash
./configure
make
sudo make install
```
去除apt锁
```bash
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/dpkg/lock
```