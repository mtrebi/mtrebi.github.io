---
layout: post
title: "Row major vs Column major matrices"
author: "Mariano Trebino"
meta: "Girona"
---

## Definition of row/column vectors

For coherence and to make things easier to understand there are two ways to write vectors. We can write them horizontally (row vector) or vertically (column vector). 

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/2017-01-20-row-vs-column/row-vector.PNG"> </p>
_Row vector RV_

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/2017-01-20-row-vs-column/column-vector.PNG"> </p>
_Column vector CV_

When working with vectors, this is purely aesthetic. In fact we can say that RV = CVT and vice versa. Most math books use the column vector notation and then use its transpose CVT to include the vector in a paragraph or sentence.

## Definition of row/column major matrices

Another common convention is work with row major matrices or column major matrices. As you may guessed, a row major matrix is made up of row vectors and a column major matrix is made up column vectors. 


<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/2017-01-20-row-vs-column/row-major-matrix.PNG"> </p>
_Row major matrix RM_

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/2017-01-20-row-vs-column/column-major-matrix.PNG"> </p>
_Column major matrix CM_

As before, the expression RM = CMT holds. Note that the definition of row/column major matrix only has sense when the elements of the matrix are actually vectors. This means that the elements in the same row (in the case of row major) or same column (in the case of column major) have a relationship. They are tied together so it makes sense to display them together.

## Why is this important?

By now, all this information hasn't been useful at all. Let's see what happens when we multiply a row vector RV by a row major matrix RM and a column vector CV with a column major matrix CM respectively.

_RV1x3 · RM3x3 = RV'1x3_

The result of product between a row vector and a row major matrix is another row vector.

_CM3x3 · CV3x1= CV'3x1_

The same holds in the case of a column vector and a column major matrix. Recalling the previous definitions:

RV = CVT
RM = CMT

We can say that RV'1x3= CV'3x1T and it's very easy to demonstrate:

_RV1x3 · RM3x3 = CV'3x1T_
_(RV1x3 · RM3x3 )T= CV'3x1_
_RM3x3T · RV1x3T = CV'3x1
_CM3x3 · CV1x3 = CV'3x1_

Notice here that when we multiply __row vectors and row major matrices__, the vector is always at the __left-most side__ because of the constraints of the matrix multiplication. On the other hand, when we multiply __column vectors and column major matrices__, the vector is always at the __right-most side__. 

This is important to understand and truly relevant when using matrices to perform transformations (rotations, translations, scales...) on vectors. Imagine that we have a vector V of size 3 that represents a point in a 3D space. We can express it as RV1x3 or CV3x1. Now, we want to perform some sequence of operations on this vector. First a translation T (RT and CT respectively) and then a rotation R (RR and CR). If we perform this operation following the "row scheme":

In row scheme:

_RV1x3 · RT3x3 · RR3x3 = RV'1x3_

In column scheme:

_RR3x3 · RT3x3 · CV3x1 = CV'3x1_

Do you see the difference now? In the row scheme the vector stays at the left-most part of the equation and the __multiplications are performed in order__. First the translation and then the rotation. However, in the column scheme the vector stays at the right-most part and the __multiplications are performed in the reverse order__: first we multiply by the rotation and then by the translation matrix.

None of this scheme is better than the other. The result is always the same (transposed but it's still the same). Just __make sure that you know if you are working with columns or rows__  before multiplying matrices.

## References:

Fletcher Dunn, Ian Parberry: “3D Math Primer for Graphics and Game Development"