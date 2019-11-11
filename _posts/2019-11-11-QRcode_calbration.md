---
layout: post
title: 相机标定
date: 2019-11-11
tags: ground_truth_estimation_2d
---

## 1.相机标定

### 1.1 安装摄像头驱动和标定工具包

> sudo apt-get install ros-kinetic-usb-cam
> sudo apt-get install ros-kinetic-camera-calibration  ## 标定工具包


标定需要用到棋盘格标定靶，点击此处[查看下载标定靶](https://github.com/danielzph/ros_exploring/tree/master/robot_perception/robot_vision/doc),里面checkboard.pdf文件。

### 1.2 开始标定

> roslaunch robot_vision usb_cam.launch    ##利用launch文件启动摄像头

> rosrun camera_calibration cameracalibrator.py --size 8x6 --square 0.024 image:=/usb_cam/image_raw camera:/usb_cam    ##启动标定程序

`size 8x6` 表示棋盘格内部角点数，即6行，每行8个角点。  
`square 0.024` 表示棋盘格边长，单位为米。   

标定程序启动成功后，将标定靶放置在摄像头视野范围内，左右、上下、前后、倾斜运动。直到“CALIBRATE”按钮变色，表示参数采集完成，点击“CALIBRATE”按钮，开始计算标定参数，此时需要等待一段时间，成功后，点击“SAVE”按钮，完成标定。

在/tmp/calibrationdate.tar.gz压缩包解压后，找到ost.yaml文件，将其复制出重新命名即可使用。







<br>

转载请注明：[张鹏辉的博客](http://danielzph.github.io) >> [相机标定](https://danielzph.github.io/2019/11/QRcode_calbration/)



