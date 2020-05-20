---
layout:     post
title:      "3D Point Cloud"
subtitle:   " \"Interview Prep\""
date:       2020-05-20
author:     "Koala"
header-img: "img/post-bg-universe.jpg"
catalog: true
tags:
    - graphics
---

> “3D点云处理”<br>

参考资料：

* **[3D点云综述]( https://blog.csdn.net/john_bh/article/details/103804177) ** 
* **[深度学习在3D点云处理中的探索](https://www.bilibili.com/video/BV1et411F78Y?from=search&seid=9625151677970010889)**
* **3D is here: Point Cloud Library (PCL)**

## 点云是什么

* 某个坐标系下点的数据集
* 包含了丰富的信息，包括三维坐标X，Y，Z、颜色、分类值、强度值、时间等

## 获取途径

主要是通过三维激光扫描仪进行数据采集获取点云数据，其次通过二维影像进行三维重建，在重建过程中获取点云数据，另外还有一些，通过三维模型来计算获取点云。

Light Detection And Ranging (LIDAR)

## Intro

* 点云深度学习包括：3D形状分类，3D对象检测和跟踪以及3D点云分割(3D shape classification, 3D object detection and tracking, and 3D point cloud segmentation)
* 3D数据的存储格式：深度图像，点云，网格和体积网格；点云表示将原始几何信息保留在3D空间中，而不会进行任何离散化
* 在3D点云上进行深度学习仍然面临数个重大挑战，例如数据集规模小，维数高和3D点云的非结构化性质

## PCL

Point Cloud Library

PCL provides support for all the common 3D building blocks that applications need. 

The library contains state-of- the art algorithms for: filtering, feature estimation, surface reconstruction, registration, model fitting and segmentation. PCL is supported by an international community of robotics and perception researchers(点云获取、滤波、分割、配准、检索、特征提取、识别、追踪、曲面重建、可视化).

* Robots need to be able to perceive the world
* PCL helps robots and provides mechanism for handling point clouds efficiently
* PCL is for n-D Point Clouds and 3D geometry processin
* PCL is fully integrated with ROS, the Robot Operating System (see http://ros.org)

