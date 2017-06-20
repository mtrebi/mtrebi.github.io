---
layout: page
title: Projects
permalink: /projects/
---

### Thread Pool

Thread pool implemented in C++11 using Threads, Futures, Packaged Tasks and type deductions

[Read more](https://github.com/mtrebi/thread-pool)

### Software rasterizer

After a small OpenGL project I decided to implement my own OpenGL rendering pipeline in the CPU in order to understand how it works. The goal of this project was not to create a next generation renderer but to understand how the rendering algorithms transforms a set of vertices that make up a 3D World into a 2D image of that World.

For this project I started by implementing a very basic rasterizer to render a simple triangle and then I added more and more features like:

* Camera and Object transformations using 4x4 homogeneous matrices
* Rotations using Euler angles and Quaternions
* Affine and Perspective corrected mapping for textures
* Orthographic and Perspective camera
* Phong and Blinn-Phong shading given material phong coefficients
* Phong and Blinn-Phong shading given material diffuse and specular textures
* Normal mapping
* Simple optimizations
* A depth-buffer to solve the visibility surface problem
* Two rendering paths: Forward and deferred
* Shadow mapping for directional lights with PCF 

<p align="center">  <img src="https://github.com/mtrebi/Rasterizer/blob/master/docs/images/gallery/textured_vs_flat_scene.png?raw=true"> </p>

[Read more](https://github.com/mtrebi/Rasterizer)




### Memory allocators

### OpenGL app

### Software raytracer

### MSc. thesis: AI system to simulate combat behaviors in FPS
MSc. thesis: AI system for simulating combat behaviors in FPS games using Behavior Trees, visibility algorithms, and influence maps in Unreal Engine 4




### Bug0 navigation algorithm for Turtlebot 2.0

Bug0 navigation algorithm in Python to move a Turtlebot 2 from one point to another avoiding obstacles using the depth sensor of XBOX Kinect

### Android app

Unofficial android app to vote for the 9N Referendum in Catalonia and generate demographics statistics