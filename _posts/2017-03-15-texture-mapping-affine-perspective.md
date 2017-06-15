---
layout: post
title: "Texture mapping: Affine vs Perspective"
author: "Mariano Trebino"
meta: "Girona"
---
## Definition

Texture Mapping is the process of mapping a 2D texture into a 3D surface in order to add more details.

To do so, each vertex in an object has assigned a texture coordinate. As always, the attributes, in this case, the texture coordinates, of the fragments between the vertices are calculated using some kind of interpolation.

## Affine interpolation

The cheapest way to interpolate between the three texture coordinates of a triangle is using a linear interpolation with Barycentric Coordinates. This seems to work:

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/2017-03-15-texture-mapping-affine-perspective/affine_mapping.PNG"> </p>

The implementation is very straightforward because the interpolation is performed in 2D screen space: 

```c++
const Vector2D calculateTextureCoords(const Triangle2D& triangle_screen, const Point2D& pixel_screen) {
  double u, v, w;
  triangle_screen.calculateBarycentricCoords(u, v, w, pixel_screen);
 
  const Vector2D texture_coords =
    triangle_screen.v1.texture_coords * u +
    triangle_screen.v2.texture_coords * v +
    triangle_screen.v3.texture_coords * w;
 
  return texture_coords;
}
```

However, this type of interpolation only works well when there is no perspective distortion. Look at what happens when we use affine mapping with an object that is distorted due to perspective projection:

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/2017-03-15-texture-mapping-affine-perspective/affine_mapping_distorted.PNG"> </p>

This happens because, when performing linear interpolation of textures, we're just interpolating a 2D projection of the vertices that does not take into account the Z coordinate. All texels have the same size so they are no affected by depth. In order to solve this problem, we need to use a different type of interpolation that does take into account the value of Z.

## Perspective corrected interpolation

The idea of perspective corrected interpolation is to, instead of interpolating in 2D space, do it in 3D space, taking into account the Z coordinate. This way, we are able to sample less texture coordinates near the camera, and sample more for points farther away. This causes the texture to be stretched and become wider near the camera and to be compressed and become smaller when it is far, giving a much better result:

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/2017-03-15-texture-mapping-affine-perspective/perspective_corrected_mapping.PNG"> </p>

The For me, the easiest way to implement this is to perform interpolation in 3D instead of doing it in 2D. So, instead of using a projected 2D triangle and a projected 2D point like in affine mapping, I use the 3D coordinates of the triangle and the 3D coordinates of the pixel to calculate the interpolation: 

```c++
const Vector2D calculateTextureCoords(const Triangle3D& triangle_world, const Point3D& pixel_world) {
  double u, v, w;
  triangle_world.calculateBarycentricCoords(u, v, w, pixel_world);
 
  const Vector2D texture_coords =
    triangle_world.v1.texture_coords * u +
    triangle_world.v2.texture_coords * v +
    triangle_world.v3.texture_coords * w;
 
  return texture_coords;
}
```

Another way to achieve this is by linearly interpolating U and V and then dividing them by Z. Then, we also interpolate 1/Z  and we use this result to divide again U and V to get the final value of the texture coordinates.