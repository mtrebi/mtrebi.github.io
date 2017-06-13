---
layout: post
title: "The Rendering Equation"
author: "Mariano Trebino"
meta: "Girona"
---
## Definition

The __rendering equation__ is a function to describe the behavior that light should follow in order to create physically-realistic images. If a rendering satisfy this function, that means that is simulating the light as it behaves in our real world (almost):

<p align="center">  <img src="https://github.com/mtrebi/mtrebi.github.io/blob/master/assets/2017-01-18-the-rendering-equation/equation_complete.PNG"> </p>

At first, this equation may seem complex, but it is quite easy to understand. However, its computation it's way more complicated. Let's start analyzing part by part:

<p align="center">  <img src="https://github.com/mtrebi/mtrebi.github.io/blob/master/assets/2017-01-18-the-rendering-equation/equation_left.PNG"> </p>

Radiance leaving at surface point X in direction Wout. If X is a visible point and Wout points to the eye (or camera) then, this is how we determine the pixel color.

<p align="center">  <img src="https://github.com/mtrebi/mtrebi.github.io/blob/master/assets/2017-01-18-the-rendering-equation/equation_emissive.PNG"> </p>


Radiance emitted at point X in direction Wout. For non-emmisive objects this is zero.

<p align="center">  <img src="https://github.com/mtrebi/mtrebi.github.io/blob/master/assets/2017-01-18-the-rendering-equation/equation_integral.PNG"> </p>

This is probably the most confusing part so let's split it again:

<p align="center">  <img src="https://github.com/mtrebi/mtrebi.github.io/blob/master/assets/2017-01-18-the-rendering-equation/equation_integral_summary.PNG"> </p>

This calculates how much radiance is reflected towards Wout. For now we have that:

<p align="center">  <img src="https://github.com/mtrebi/mtrebi.github.io/blob/master/assets/2017-01-18-the-rendering-equation/equation_integral_explained.PNG"> </p>

Then, the ingteral integrates (hoho) the light of all possible incoming directions Win in the hemisphere Ω and we end up with:

<p align="center">  <img src="https://github.com/mtrebi/mtrebi.github.io/blob/master/assets/2017-01-18-the-rendering-equation/equation_integral_explained2.PNG"> </p>

This means that for each Win we determine how much it contributes to the amount of light reflected in the Wout direction.

<p align="center">  <img src="https://github.com/mtrebi/mtrebi.github.io/blob/master/assets/2017-01-18-the-rendering-equation/equation_light_incoming.PNG"> </p>

Radiance incident at surface point X coming from Win direction.

<p align="center">  <img src="https://github.com/mtrebi/mtrebi.github.io/blob/master/assets/2017-01-18-the-rendering-equation/equation_brdf.PNG"> </p>


Radiance at point X from Win direction that is reflected in Wout direction (see [The BRDF post](https://mtrebi.github.io/2017/01/18/the-brdf.html))

<p align="center">  <img src="https://github.com/mtrebi/mtrebi.github.io/blob/master/assets/2017-01-18-the-rendering-equation/equation_lambert.PNG"> </p>

The dot product of this two normalized vectors (Win is negated because it's an incoming ray and it should be outgoing) returns its angle. When this angle is 90º (vectors are perpendicular) all the radiance from Win is received by the object. However, when the angle is 0º (vectors are parallel), the radiance is minimized at it's equal to zero. This is the [Lambert factor](https://en.wikipedia.org/wiki/Lambert's_cosine_law). And that's all. It's very intuitive but it may seem scary at first. 

Before finishing the post I would like to talk why this equation is so complex. As we saw, to calculate the reflected light in one specific direction Wout we need to calculate the incoming light for all incoming directions. And this is hard for two reasons:
- The number of incoming directions is infinite. This isn't too bad. We just sample and use a high number of different directions.
- The amount of light for a specific incoming direction in a surface can be light that comes directly from a light sources (direct illumination) or reflected light (indirect illumination). Direct illumination is easy to calculate but indirect is not. This is because when reflected light from a surface B hits a surface A, the amount of light at A depends on all of the incoming directions of light in the surface B. And also, the incoming light of B depends on all of the incoming directions of light at C and A. __This process is recursive and infinite__ and is the reason why this is so hard to simulate. There is a field in rendering called __global illumination__ that studies how to calculate (or should I say, approximate) indirect illumination.

## References

Fletcher Dunn, Ian Parberry: “3D Math Primer for Graphics and Game Development"