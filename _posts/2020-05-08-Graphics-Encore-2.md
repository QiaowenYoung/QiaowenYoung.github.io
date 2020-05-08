---

layout:     post

title:      "Graphics Encore(2)"

subtitle:   " \"Review for an Interview\""

date:       2020-05-08

author:     "Koala"

header-img: "img/post-bg-unix-linux.jpg"

catalog: true

tags:

​    \- graphics

​    \- review

---



\> “Words, don't come easy to me”

<p id = "build"></p>

## Transformation

* **transformation matrix**

  assume that vector is row vector and multiplies matrix from the left

  more specifically, assume vector is $[x, y, 1]$ in 2D

  rotate: $R=$ $$ \begin{bmatrix}cos\theta &sin\theta &0 \\ -sin\theta &cos\theta &0 \\ 0 &0 &1 \end{bmatrix}$$ $=>[xcos\theta-ysin\theta, xsin\theta+ycos\theta, 1]$

  panning: $P=$ $$ \begin{bmatrix}1 &0 &0 \\ 0 &1 &0 \\ L &0 &1 \end{bmatrix}$$ $=>[x+L,y,1]$

  scaling: $S=$ $$ \begin{bmatrix}\alpha &0 &0 \\ 0 &\alpha &0 \\ 0 &0 &1 \end{bmatrix}$$ $=>[\alpha x, \alpha y, 1]$

  shear: $S=$ $$ \begin{bmatrix}1 &0 &0 \\ cot\theta &1 &0 \\ 0 &0 &1 \end{bmatrix}$$ $=>[x+ycot\theta, y, 1]$

* **camera transformation**

  world->camera->view

  world and camera are right hand coord system, view the left; this is because we are used to set our view direction as $z$ axis, right hand as $x$ axis, and our head up as $y$ axis

## Ray Tracing

trace the light from eyes instead of from lighting sources

instead of calculating each pixel from light source to eye, ray tracing does it backward

use recursive method; send out a ray into the scene, calculate the closest intersection between light and polygons; if the material of this intersection is reflective or refractive, can recursively trace it down, until meeting light source or the maximum recursive depths

Reference: [ray tracing 入门](https://yangwc.com/2019/05/08/RayTracer-Basis/)

