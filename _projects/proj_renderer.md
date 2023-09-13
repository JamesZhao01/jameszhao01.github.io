---
layout: page
title: Cpu Recursive Ray Tracer
description: CSE167 - Computer Graphics - Final Project
img: assets/img/cse167/render/enviro_mountain.png
importance: 1
category: Projects
---

Within
<a href ="https://cseweb.ucsd.edu//~viscomp/classes/cse167/wi23/index.html">CSE
167: Computer Graphics</a>, I developed both a (1) bezier and bspline 3d
modeling program, and (2) a CPU-based recursive ray tracer

# 3d Curve Modeling Program

Using OpenGL and C++, I constructed a program capable of both visualizing
B-Spline and Bezier Curves, as well as revolving the curves to generate a mesh,
arbitrary 3rd transforms to the meshes, and rotating the camera view (through
transformations of the ModelView matrix)

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse167/amphora.png" title="amphora" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse167/ghost.png" title="ghost" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse167/icecream.png" title="icecream" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm-3 mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse167/emblem.png" title="emblem" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-3 mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse167/lux_wand.png" title="lux_wand" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include video.html path="assets/video/cse167/basic_apple_demo.mp4" title="demo" class="img-fluid rounded z-depth-1" controls="true" %}
    </div>
</div>

<div class="caption">
  Model program examples
</div>

# CPU Recursive Ray Tracer

Using C++, I, along with my <a href="https://www.jettbui.dev/">partner, Jett
Bui,</a>, also constructed a recursive ray tracer.

The raytracer assignment originally featured basic functionality, including
creating scenes of geometric primitives (triangles, spheres) with reflective
raytracing. Using optimizations of octree and multiprocessing, we were able to
achieve a 160x speedup for complicated scenes (including the
<a href ="https://en.wikipedia.org/wiki/Stanford_dragon">Stanford Dragon</a>)

As a part of extensions of the project, we added:

- Normal Mapping
- Environment Mapping (skybox cubemap)
- Texture color mapping w/ Nearest-Neighbor and linear interpolation
- Anti Aliasing
- Soft Shadows
- Snell's Law Refractions

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse167/render/enviro_hellfire.png" title="hellfire" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse167/render/enviro_mountain.png" title="mountain" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse167/render/normal.png" title="normal" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse167/render/scene7-refract.png" title="refract" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse167/render/shadows-area.png" title="shadows" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse167/render/teapot-64x.png" title="teapot-64x" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse167/render/teapot-mountain.png" title="teapot-mountain" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse167/render/texture-normal.png" title="texture-normal" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="caption">
  Raytracing results gallery
</div>
