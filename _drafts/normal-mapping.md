---
layout: post
title: "Normal mapping"
author: "Mariano Trebino"
meta: "Girona"
---

## Definition

The purpose of  normal maps is to increase the details of a surface by giving a per texel normal instead of a per vertex normal. This is very similar to diffuse or specular maps but, instead of getting a color, we get a normal vector. The improvement in quality is noticeable:

<p align="center">  <img src="https://raw.githubusercontent.com/mtrebi/mtrebi.github.io/master/assets/XXXX-XX-XX-normal-mapping/blinn_phong_textured_normal_map.bmp"> </p>


## Calculation

The implementation of normal maps it's quite easy but it is not as straightforward as color textures for one simple reason.

[Explain Tangent space]

So, what we do is, we calculate the basis vectors of the Tangent Space (tangent, bitangent and normal), we get the normal vector from the texture and we convert it from Tangent Space into World Space:
```c++
const Vector3D getNormal(const Triangle3D& triangle_world, const Vector2D& text_coords) const { 
  Vector3D tangent, bitangent;
  calculateTangentSpace(tangent, bitangent, triangle_world);
 
  const Vector3D normal_tangent = (Vector3D) getTextureColor(m_texture_normal, m_texture_normal_width, m_texture_normal_height, text_coords);
  const Vector3D normal_world = TangentToWorld(normal_tangent, tangent, bitangent, triangle_world.normal);
  
  return normal_world;
}
```

We calculate the basis vectors of the Tangent Space:

```c++
void calculateTangentSpace(Vector3D& tangent, Vector3D& bitangent, const Triangle3D& triangle_world) {
  const Vector3D q1 = triangle_world.v2.position - triangle_world.v1.position;
  const Vector3D q2 = triangle_world.v3.position - triangle_world.v2.position;
 
  const double s1 = triangle_world.v2.texture_coords.x - triangle_world.v1.texture_coords.x;
  const double s2 = triangle_world.v3.texture_coords.x - triangle_world.v2.texture_coords.x;
 
  const double t1 = triangle_world.v2.texture_coords.y - triangle_world.v1.texture_coords.y;
  const double t2 = triangle_world.v3.texture_coords.y - triangle_world.v2.texture_coords.y;
 
 
  tangent = t2 * q1 - t1 * q2;
  bitangent = -s2 * q1 + s1 * q2;
 
  tangent.normalize();
  bitangent.normalize();
}
```

Then, we finally transform the vector expressed tangent space into world space.

```c++
const Vector3D TangentToWorld(const Vector3D& v, const Vector3D& tangent, const Vector3D& bitangent, const Vector3D& normal) {
  // V * TBN
  Vector3D v_world = {
    v.x * tangent.x + v.y * bitangent.x + v.z * normal.x,
    v.x * tangent.y + v.y * bitangent.y + v.z * normal.y,
    v.x * tangent.z + v.y * bitangent.z + v.z * normal.z,
  };
 
  v_world.normalize();
 
  return v_world;
}
```