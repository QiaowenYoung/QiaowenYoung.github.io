---
layout:     post
title:      "Graphics Encore(1)"
subtitle:   " \"Review for an Interview\""
date:       2020-05-07
author:     "Koala"
header-img: "img/about-bg-walle.jpg"
catalog: true
tags:
    - graphics
    - review
---

> “加油阿考”

打开了熟悉的[CSE160](https://users.soe.ucsc.edu/~pang/160/f19/schedule.html)，怀念艰难又快乐的画树时光。大学至此，没有比在加州更好的日子了。

参考书：[Angel & Shreiner: Online examples](http://www.cs.unm.edu/~angel/WebGL/7E/)


<p id = "build"></p>

## Lighting & Shading

* **vertex shader and fragment shader**

  vertex: describe vertices' features, like position and color

  fragment: fragment is like a pixel, a unit of an image

* **ambient, diffuse and specular lighting**

  ambient: the light that is already present in a scene, before any additional lighting is added

  diffuse: scattered and comes from all directions

  specular: identifies the bright specular highlights that occur when light hits an object surface and reflects back toward the camera

* **flat shading, gouraud shading and phong shading **

  flat: all of the polygons reflect as a flat surface, giving a blocky look and feel to a model

  gouraud: smooth shading, per-vertex, vertex shader get color passed to fragment shader

  phong: smooth shading, per-fragment, vertex shader passed position and normal to fragment shader

* **formula**

  $I_d = IK_dcos\theta$

  $I_a = IK_a$

  $I_s = IK_scos^n\alpha$

  $\vec H = \vec L + \vec V$

  $\hat R = 2\hat N(\hat N \cdot\vec L)-\vec L$

  $I_4 = \frac{y_4-y_2}{y_1-y_2}I_1+\frac{y_1-y_4}{y_1-y_2}I_2$

  $I_p = \frac{x_5-x_p}{x_5-x_4}I_4+\frac{x_p-x_4}{x_5-x_4}I_5$

  $I$: light color, 1 * 3 vector, rgb

  $\theta$: angle between lighting and normal

  $\alpha$: angle between reflection light and view

  $n$: glosiness factor; the larger it is, the brighter and smaller the reflective point will be

  $\hat H$: half vector of light direction and view direction

  $\hat R$: based on light direction and normal, calculate reflective light's direction

  last two lines: linear interpolation for gouraud shading

## Parametric Curves

* **linear, quadratic and cubic**

  > Example: Given 3 pts, $p_0, p_1, p_2$
  >
  > $p(t)=at^2+bt+1=[t^2, t, 1]MG$
  >
  > $G=[p0, p1, p2]^T$

  linear: 2pts

  quadratic: 3 pts

  cubic: 4 pts

* **interpolation**

  > Example: solve $c$ in $p(u)=u^Tc$, such that $p(u)$ interpolates the given 4 pts
  >
  > $p_0=p(0)=c_0$
  >
  > $p_1=p(\frac{1}{3})=c_0+\frac{1}{3}c_1+(\frac{1}{3})^2c_2+(\frac{1}{3})^3c_3$
  >
  > $p_2=p(\frac{2}{3})=c_0+\frac{2}{3}c_1+(\frac{2}{3})^2c_2+(\frac{2}{3})^3c_3$
  >
  > $p_3=p(1)=c_0+c_1+c_2+c_3$

  Write the above functions as below:

  $p=Ac$, where $p=[p0, p1, p2, p3]^T$

  and $A$ is a matrix containing all the coefficients

  can calculate inverse matrix of $A$ to get $c$

  suppose $M = A^{-1}$, then $c=Mp$

  interpolation can also be used in bicubic surface patch

* **blending function**

  $p(u)=u^Tc=u^TMp=b(u)^Tp$

  where $b(u)=M^Tu=[b_0(u), b_1(u), b_2(u), b_3(u)]^T$

  $p(u)=b_0(u)p_0+b_1(u)p_1+b_2(u)p_2+b_3(u)p_3=\sum^3_{i=0}b_i(u)p_i$

* **Hermite, Bezier, B-Splines**

  they are 3 types of curves with different $M$

  Hermite: suppose we have $p_0$ and $p_3$, and the derivative value at $u=0$ and $u=1$, need to solve difference control point at $u=0$ and $u=1$

  $M_H=\left[ \begin{matrix}   1 & 0 & 0 & 0 \\   0 & 0 & 1 & 0 \\   -3 & 3 & -2 & -1\\2&-2&1&1 \end{matrix}  \right]$

  Bezier: use 4 pts again, but 2 of them control the derivative values at $u=0$ and $u=1$

  $M_B=\left[ \begin{matrix}   1 & 0 & 0 & 0 \\   -3 & 3 & 0 & 0 \\   3 & -6 & 3 & 0\\-1&3&-3&1 \end{matrix}  \right]$

  B-Splines: I can't understand

  $M_S=\frac{1}{6}\left[ \begin{matrix}   1 & 4 & 1 & 0 \\   -3 & 0 & 3 & 0 \\   3 & -6 & 3 & 0\\-1&3&-3&1 \end{matrix}  \right]$

  

