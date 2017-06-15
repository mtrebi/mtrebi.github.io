---
layout: post
title: "Barycentric space (II): Calculation"
author: "Mariano Trebino"
meta: "Girona"
---

## Introduction

In the previous post Barycentric space (I): Definition I explained what Barycentric Coordinates are. Now, we're going to see how can we calculate them.

## Calculation

Let's say that we want to calculate the barycentric coords (b1, b2, b3) of the point P. 

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/2017-03-13-barycentric-space-ii/barycentric_coords_p.PNG"> </p>

Since we know the coortdinate v1, v2, v3 and P we have three equations and three unknowns:

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/2017-03-13-barycentric-space-ii/barycentric_coords_formula.PNG"> </p>

Solving this equation yields:

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/2017-03-13-barycentric-space-ii/barycentric_coords_formula_solution.PNG"> </p>

This shows an interesting property of barycentric coordinates: they are equivalent to the signed ratio of the area.

There are many ways to calculate the signed area of a triangle, probably, the easiest one is using the cross product. Remember that the cross product between two vectors gives the signed area of the parallelogram they define. Dividing it by 2 we have the area of the triangle.

In the image below all edges of the different triangles are defined.

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/2017-03-13-barycentric-space-ii/barycentric_coords_p2.PNG"> </p>


Using this information and simplifying the equations (because numerator and denominator are divided by 2) we get the final formulas of the barycentric coordinates:

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/2017-03-13-barycentric-space-ii/formula_final.PNG"> </p>

## Calculation

If you are really worried about efficiency, take a loot at this stackoverflow question about how to do it.

```c++
void calculateBarycentricCoords(double& u, double& v, double& w, const Point2D& point) const {
  const Vector2D v0 = this->v2 - this->v1, v1 = this->v3 - this->v1, v2 = point - this->v1;
  double d00 = v0 * v0;
  double d01 = v0 * v1;
  double d11 = v1 * v1;
  double d20 = v2 * v0;
  double d21 = v2 * v1;
  double denom = d00 * d11 - d01 * d01;
  v = (d11 * d20 - d01 * d21) / denom;
  w = (d00 * d21 - d01 * d20) / denom;
  u = 1.0f - v - w;
}
```