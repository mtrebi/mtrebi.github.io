---
layout: page
title: Projects
permalink: /projects/
---
## Table of contents
&nbsp;[2017](https://mtrebi.github.io/projects/#2017)  <br/> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Procedural Generation using WCF](https://mtrebi.github.io/projects/#procedural-generation-using-wcf-in-progress)  <br/> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Thread Pool](https://mtrebi.github.io/projects/#thread-pool)  <br/> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Multi-threading matrix multiplication](https://mtrebi.github.io/projects/#multi-threading-matrix-multiplication)  <br/> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Software Rasterizer](https://mtrebi.github.io/projects/#software-rasterizer)  <br/> 
&nbsp;[2016](https://mtrebi.github.io/projects/#2016)  <br/> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Memory allocators](https://mtrebi.github.io/projects/#memory-allocators)  <br/> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Basic OpenGL project](https://mtrebi.github.io/projects/#basic-opengl-project)  <br/> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Software Raytracer](https://mtrebi.github.io/projects/#software-raytracer)  <br/> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[MSc. thesis: AI system to simulate combat behaviors in FPS](https://mtrebi.github.io/projects/#msc-thesis-ai-system-to-simulate-combat-behaviors-in-fps)  <br/> 
&nbsp;[2015](https://mtrebi.github.io/projects/#2015)  <br/> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Bug0 navigation algorithm for Turtlebot 2.0](https://mtrebi.github.io/projects/#bug0-navigation-algorithm-for-turtlebot-20)  <br/> 
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Android app to vote for the 9N Catalonian referendum](https://mtrebi.github.io/projects/#android-app-to-vote-for-the-9n-catalonian-referendum)  <br/> 
## 2017
<hr>
### Procedural Generation using WCF (in progress)

_C#, Unity, WCF, Voxel Art_

This is my last project and it's currently under development. I wanted to do something with Unity and Procedural Generation so I am implementing a Wave Collapse Function to procedurally generate things. My final goal is to procedurally generate buildings and cities but for now I just managed to generate 2D terrain.

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/WaveCollapseFunction/master/Docs/Videos/wang_tiles_generation.gif?raw=true" width="400"> </p>

[Read more](https://github.com/mtrebi/WaveCollapseFunction)

### Thread Pool

_C++, Multi-threading, Semaphores, Futures_

After the multi-threading matrix multiplication project I decided to dig deeper into this topic and try to create something cool and useful. I ended up with the idea of a Thread Pool.

From Wikipedia:
> In computer programming, a thread pool is a software design pattern for achieving concurrency of execution in a computer program. [...] A thread pool maintains multiple threads waiting for tasks to be allocated for concurrent execution by the supervising program. By maintaining a pool of threads, the model increases performance and avoids latency in execution

And that's what I did. I created a generic thread pool in C++11 that can take a function with an arbitrary signature and returns a future. This future will be solved with the result of the function as soon as the thread pool has an available thread to execute it.

[Read more](https://github.com/mtrebi/thread-pool)

### Multi-threading matrix multiplication

_C++, Multi-threading_

In order to review my multi-threading skills and learn about the "new" thread class in C++11 I decided to implement this simple program. 

My idea was to compare two different implementations, one sequential vs one multi-thread to see how much improvement there is. The problem I choose was matrix multiplication.

The sequential algorithm is quite straightforward. The multi-threading one is a little bit tricky. The idea is to split the matrix in independent parts that can be handled by one unique thread avoiding syncronization and increasing performance.

[Read more](https://github.com/mtrebi/https://github.com/mtrebi/matrix-multiplication-threading)

### Software rasterizer

_C++, 3D Graphics, Rendering_

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

## 2016
<hr>
### Memory allocators

_C++, Memory Management_

After talking about memory management in games with a fellow RC during my time in New York I decided to research about it and I ended up implementing serveral memory allocators (linear, stack, pool and free list).

Developing a custom allocator was quite tricky because I had to implement by myself how memory was stored and managed with the allocate and free operations. Meta data must be kept to a minimum and data must be always aligned.

After implementing all of this, I compared the performance of my allocators against malloc using custom benchmarks. It turned out that all my allocators were way better than malloc.


Checkout also the [slides](https://github.com/mtrebi/memory-allocators/blob/master/docs/Dynamic%20memory(I).pdf) I used for a 5-min presentation I gave at the RC

[Read more](https://github.com/mtrebi/memory-allocators)

### Basic OpenGl project

_C++, OpenGL_

Very basic project based on a series of [tutorials](https://learnopengl.com/). It was useful for me as an introduction to OpenGL. I implemented some simple features like Gouraud, Phong and Blinn-Phong Shading, Rim lighting, normal mapping and shadow mapping.

<p align="center">  <img src="https://github.com/mtrebi/rendering-engine/blob/master/docs/images/rim_lighting.PNG?raw=true" width="400"> </p>

### Software raytracer

_C++, 3D Graphics, Rendering_

The goal of this project was to become familiar with C++ and graphics stuff while having fun. It was a really amazing project and I encourage everyone to do it if you like graphics. My raytracer is a backwards raytracer. Is quite basic and simple and includes the following features:

- Basic shapes: Planes and Spheres.
- Shadows: Simulate shadows using Shadow Rays to multiple light sources. The shadows can be softer or harder depending on the number of lights that illuminate them.
- Phong illumination model to simulate simulate ambient, colored diffuse and colored specular illumination.
- Mirror reflection: Perfect reflection for mirrors.
- Refraction: Refraction of light depending on the refraction index of the materials.
- Anti-aliasing: Regular sampling technique.
- Multiple cameras: perspective and orthogonal.
- Easy to extend. I took care to design the raytracer folowing the software principles. It is very to modify or extend any of the previous features, for example, to add another material, camera or sampling method.

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/Raytracer/master/docs/images/final-256-sampling.bmp" width="400"> </p>

[Read more](https://github.com/mtrebi/Raytracer)

### MSc. thesis: AI system to simulate combat behaviors in FPS

_C++, Unreal Engine 4, Artificial Intelligence, Behavior Trees_

The aim of this project was to build an AI system for an existing game. To do so, I replaced the AI system of the Shooter Game provided by the Library of Unreal Engine 4 with my own AI system. 

This system was based on UE4 Behavior Trees with many custom nodes created in C++ and also in modifications  on  to add interesting features:

- Tactical pathfinding. I modified the A* navigation algorithm of UE4 to modify the cost heuristic based on the the areas that were visible by the player (I implemented a custom visibility algorithm to determine this).
- Player prediction. In order to calculate the most probable position of the player after a certain time without seeing him, I implemented my custom Influence Maps.
- Group behavior. I shared some information between the different bots to attack from different sides or spreading out on the map when searching.
- Positioning. I created custom EQS queries to test whether a position was good cover or a good attack position, or if it was close to an obstacle...

<p align="center"> <a href="https://www.youtube.com/watch?v=fTocYPT-k6o&list=PLeGS7otZ9mSexXzFVHJJb5Oaj1MCPA3rA&index=1"><img src="http://img.youtube.com/vi/wSTioum0eas/0.jpg" title="Youtube playlist with demo videos" width="400" /></a> </p>

[Read more](https://github.com/mtrebi/AI_FPS)

## 2015
<hr>
### Bug0 navigation algorithm for Turtlebot 2.0

_Python, Navigation_

I developed this project along with two students as the final project for a Robotics and VIsion subject in the university. 

We developed a Bug0 navigation algorithm for a Turtlebot 2 in Python that was able to move from the initial position to the goal position (in local space). 

We used the odometry sensors of the Turtlebot to update and correct the current position. We also took advantage of the depth sensor of the XBOX Kinect to detect obstacles. Once an obstacle was detected, the robot tried to surround it. After that, the robot re-calculated the trajectory to the goal and repetead the process.

<p align="center"> <a href="https://www.youtube.com/watch?v=7wiXgdLNfO0&list=PLeGS7otZ9mSc-kfSqJHZLcTUpjxLSWuh7&index=1"><img src="http://img.youtube.com/vi/7wiXgdLNfO0/0.jpg" title="Turtlebot avoiding bostacles" width="400" /></a> </p>

[Read more](https://github.com/mtrebi/catkin_ws)

### Android app to vote for the 9N Catalonian referendum

_Android, Java, Databases_

Two weeks before the referendum for the independence of Catalonia I met with five friends and we developed an Android application to let people vote through their smartphone and forecast the results of the referendum. We also generated basic demographics statistics to see how votes were distributed across Catalonia, age and genres.  

The [app](https://play.google.com/store/apps/details?id=com.tendevelopers.Consulta9N) is on the Playstore. However, we no longer maintain it.



