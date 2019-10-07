---
layout: post
title: minisam的编译及可能遇到的问题与解决
date: 2019-09-28
tags: minisam
---

## 一，minisam下载安装

### 1，minisam简介

    miniSAM is an open-source C++/Python framework for solving factor graph based least squares problems. The APIs and implementation of miniSAM are heavily inspired and influenced by GTSAM, a famous factor graph framework, but miniSAM is a much more lightweight framework with

    Full Python/NumPy API, which enables more agile development and easy binding with existing Python projects, and A wide list of sparse linear solvers, including CUDA enabled sparse linear solvers.

    miniSAM is developed by Jing Dong and Zhaoyang Lv. This work was initially started as final project of Math 6644 back to 2017, and mostly finished part-time when both authors were PhD students at College of Computing, Georgia Institute of Technology.


### 2，安装minisam

$ git clone https://github.com/dongjing3309/minisam.git

$ mkdir build 

$ cd build

$ cmake ..

$ make

$ make check #optional, run unit tests

## 二，我在安装编译时遇到的问题和解决办法
![](/images/posts/minisam_cmake_issues/1.png)

可能是因为sophus的版本不是最新的（或者参照老版slam十四讲或其他博客安装非模板类sophus库）导致的cmake失败。所以我接下来的做法是：卸载已经安装的sophus库，重新安装新版。
如何卸载？ 如果没有执行sudo make install，则只需要**删除原文件夹**即可；如果执行了install，则需要找到安装目录，**删除所有的安装文件**，方法可自行百度或谷歌，因为原作者并没有在makefile文件中写uninstall语句，所以执行make unintall是不可行的。

新版的sophus需要**Eigen库版本在3.3**以上，如果你曾经安装Eigen是用的是sudo apt-get install libeigen3-dev,需要检查一下你的版本是否达到要求，否则也会遇到无法编译的情况。



<br>

转载请注明：[张鹏辉的博客](http://danielzph.github.io) >> [minisam_issues](https://danielzph.github.io/2019/09/minisam_cmake_issues/)


