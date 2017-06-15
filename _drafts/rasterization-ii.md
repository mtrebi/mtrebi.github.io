---
layout: post
title: "Rasterization (II): Projection"
author: "Mariano Trebino"
meta: "Girona"
---

## Introduction

In the previous post Rasterization (I): Overview I showed you the general algorithm of a rasterizer and I introduced the different key parts that we need in order to make it work. 

```c++
Image rasterizer(const World& world) {
  /// Array of colors
  Image image(width, height);
  /// Array of distances
  DepthBuffer depth_buffer(width, height);
 
  for each triangle3D in world {
    Triangle2D triangle_projected = camera.projectTriangle(triangle3D);
    BoundingBox2D bbox_projected = calculateBBox(triangle_projected);
    for (x = bbox_projected.min.x; x <= bbox_projected.max.x; ++x) {
      for (y = bbox_projected.min.y; y <= bbox_projected.max.y; ++y) {
        Pixel pixel(x, y);
        if (triangle_projected.contains(pixel) {
          float depth = calculateDepth(triangle3D, triangle_projected, pixel);
          if (depth < depth_buffer[pixel]) {
            depth_buffer[pixel] = depth;
            image[pixel] = triangle3D.color;
          }
        }
      }
    }
  }
  return image;
}
```


In this post we are going to see, the first unknown function of the code snippet above and probably the most important function of a rasterizer, the project function. 

## Project function

As you may guessed from the code, the project function takes a 3D triangle of a 3D world and projects it into the screen generating a new 2D triangle.

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/XXXX-XX-XX-rasterization-i/projection_3d_to_screen.png"> </p>


Perspective projection of a 3D triangle into the screen creating a 2D triangle

Now that we know what the project function does, let's see how it works. To to convert from the 3D world to the 2D screen there are multiple steps involved that I believe it is worth reviewing because most graphics API use them.

The first of these steps is called the View Transform and it is a simply transformation from the World Coordinate Space to the Camera Coordinate Space.

Then, the Projection Transform is performed to convert from Camera Space to something commonly called NDC (Normalize Device Coordinates). Here is where the actual projection from 3D to 2D happens.

Finally, the Viewport Transform is applied to convert from NDC to the real window/screen size where the image will be displayed.

## View Transform

This is called view transform because we want to transform points from World Space to Camera Space. Or what it is the same, see how the points in the World look from the Camera. This can be easily accomplished with matrix multiplication. As a reminder, to convert a Point Pw expressed in World space to a point Pv expressed in Camera Space, we need a matrix M. The transformation (using row-major vectors) would be:

_Pv = Pw * M_

This matrix M defines the basis vectors of the Camera and its position expressed in World Coordinates. This matrix M is commonly known as the LookAt matrix. 

So far so good. but, how can we construct this LookAt matrix? Given the target position of the camera (where the camera is pointing to) and its position, we can build the basis vectors of the coordinate system (all should be normalized):

```c++
v_forward = (target - position);
v_forward.normalize();
 
v_right = (v_forward ^ Vector3D(0, 1, 0));
v_right.normalize();
 
v_up = v_forward ^ m_right;
v_up.normalize();
```

Then, the LookAt matrix in column-major format is:
                               

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/XXXX-XX-XX-rasterization-i/lookat_matrix.PNG"> </p>

_Note that the previous matrix is in column-major order. In row-major format is just transpose(M)_

## Project Transform

[CLIP SPLACE]
The next step would be to project the 3D points in Camera Space into Screen Space. However, before that, we're going to convert this coordinates to something called NDC (Normalized Device Coordinates) to simplify some transformations. NDC is just a simple convention to separate the projection to a generic viewport from a specific one (more on this later) creating a Normalized Coordinates of the screen.. NDC values go from -1 to 1 (OpenGL) or from 0 to 1 (DirectX). Take a look at the following picture to understand it:

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/XXXX-XX-XX-rasterization-i/normalized_device_coordinates.jpg"> </p>

So what we want is to convert out 3D points viewed from the camera to 2D points that in the range [-1, 1]. As before, we're going to use a matrix multiplication:

_Pndc = Pv * M_


The most common ways to do this is using an Orthographic or a Perspective projection.

## Orthographic camera

This is probably the easiest projection type because it has no distortion so distances and parallel lines are conserved. For these reasons, this type of projection is used in blueprints and tech draws. 

To create an orthographic projection we simply create a series of projectors from the 3D points to the 2D projection plane. All this projectors must  perpendicular to the projection plane and parallel between them. 

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/XXXX-XX-XX-rasterization-i/orthographic_projection.PNG"> </p>

## Perspective camera

## Viewport Transform

The last transform is the easiest one. We just need to convert from NDC in the range [-1, 1] to our specific viewport size (width, height). This means, scaling by our viewport dimensions and offset by viewport center:


## Putting it all together