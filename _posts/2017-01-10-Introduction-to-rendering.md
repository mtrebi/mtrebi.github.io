---
layout: post
title: "Introduction to Rendering"
author: "Mariano Trebino"
meta: "Girona"
---

## Definition

__Rendering__ is the process of generating an image from a virtual representation of a scene. An image is nothing else than a rectangular array of colors and each element in the array is a pixel (picture element). This array is known as __frame buffer__ during the rendering process.

The key point of rendering is to determine the color of each pixel of the image.  To do it, we must solve two problems:
- __Visible surface determination__. Determine the surface that is closest to the eye.
- __Lighting__. Determine the amount of light is emitted or reflected off this surface (we could say the 'brightness').
Note: There are some special cases like translucency, reflections, caustics...but let's ignore them for now.

## Visible surface determination

There are two well-known ways to determine which surface is closest to the eye (or camera). Each of these techniques deserves its own post but let's talk about them very briefly:
- Ray Tracing. The idea is to trace rays from the eye and through each pixel and check if the ray hits (intersects) any object in the scene.  If it does we get the color of the object. Otherwise we set it to a background color. This technique is used in most PBR (Physically-based rendering) and any __high-quality__ rendering.
- Depth-buffering. In this case, in each pixel along with the color, we store another value called depth. This value represents the distance from the pixel to the closest surface in the eye direction. This said, what we do is, project each object in the scene into the screen (this process is known as rasterization). Then, for each pixel of the surface (known as source fragment) we compute the depth value and we compare it with the value in the depth buffer (known as destination fragment). If the source fragment is closer from the camera than the destination fragment, we update the depth buffer with the new value.This technique is used in __real-time rendering__ (games, dynamic simulations...).

## Lighting

Once we have solved the problem of determining the closest surface and so we have the 'base' color of each pixel, we have to illuminate them (give them a certain brightness). This brightness depends on:
- __Lights__ or emissive objects. Obviously, the number of lights, its position and orientation affect the brightness.
- __Object properties__ can affect the amount of light absorbed or reflected by a specific object (checkout The BDRF post).
- __Other objects__ also affect the amount of light received by an object. This happens because light can arrive directly to the object from a light source but also indirectly. Light bounces (gets reflected) around many times in different objects.

As you may guessed, this is not a trivial task. In fact, is quite __complex__. There are many techniques to illuminate pixels: some of them are cheap but not physically-realistic (a well-known example is the Phong illumination model), others are more expensive, even some are for specific materials (like the skin).

There is an equation known as the rendering equation that defines the way to properly calculate the color of each surface point taking into account all of the previous mentioned properties to create realistic renderings.

## References:

Fletcher Dunn, Ian Parberry: “3D Math Primer for Graphics and Game Development"