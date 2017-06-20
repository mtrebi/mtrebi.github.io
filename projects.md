---
layout: page
title: Projects
permalink: /projects/
---

### Thread Pool

After the multi-threading matrix multiplication project I decided to dig deeper into this topic and try to create something cool and useful. I ended up with the idea of a Thread Pool.

Wikipedia says:
>> In computer programming, a thread pool is a software design pattern for achieving concurrency of execution in a computer program. [...] a thread pool maintains multiple threads waiting for tasks to be allocated for concurrent execution by the supervising program. By maintaining a pool of threads, the model increases performance and avoids latency in execution

And that's what I did. I created a generic thread pool in C++11 that can take a function with an arbitrary signature and returns a future. This future will be solved as soon as the thread pool has an available thread to execute the given function and calculate a result.

[Read more](https://github.com/mtrebi/thread-pool)


### Multi-threading matrix multiplication

In order to review my multi-threading skills and learn about the "new" thread class in C++11 I decided to implement this simple program. 

My idea was to compare two different implementations, one sequential vs one multi-thread to see how much improvement there is. The problem I choose was matrix multiplication.

The sequential algorithm is quite straightforward. The multi-threading one is a little bit tricky. The idea is to split the matrix in independent parts that can be handled by one unique thread avoiding syncronization and increasing performance.

[Read more](https://github.com/mtrebi/https://github.com/mtrebi/matrix-multiplication-threading)

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

The goal of this project was to become familiar with C++ and graphics stuff while having fun. It was a really amazing project and I encourage everyone to do it if you like graphics. My raytracer is a backwards raytracer. Is quite basic and simple and includes the following features:

- Basic shapes: Planes and Spheres.
- Shadows: Simulate shadows using Shadow Rays to multiple light sources. The shadows can be softer or harder depending on the number of lights that illuminate them.
- Phong illumination model to simulate simulate ambient, colored diffuse and colored specular illumination.
- Mirror reflection: Perfect reflection for mirrors.
- Refraction: Refraction of light depending on the refraction index of the materials.
- Anti-aliasing: Regular sampling technique.
- Multiple cameras: perspective and orthogonal.
- Easy to extend. I took care to design the raytracer folowing the software principles. It is very to modify or extend any of the previous features, for example, to add another material, camera or sampling method.

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/Raytracer/master/docs/images/final-256-sampling.bmp" width=400> </p>


[Read more](https://github.com/mtrebi/Raytracer)

### MSc. thesis: AI system to simulate combat behaviors in FPS
MSc. thesis: AI system for simulating combat behaviors in FPS games using Behavior Trees, visibility algorithms, and influence maps in Unreal Engine 4




### Bug0 navigation algorithm for Turtlebot 2.0

Bug0 navigation algorithm in Python to move a Turtlebot 2 from one point to another avoiding obstacles using the depth sensor of XBOX Kinect

### Android app

Unofficial android app to vote for the 9N Referendum in Catalonia and generate demographics statistics

<p align="center">  <img src="https://lh6.ggpht.com/MP30trtzQ9sUT1c0qo5lSoX1vHTT65oGHSMHF3dQtGhKGLGg3-y5kPbcs-JlJskt75Fb=h900-rw"> </p>
