---
layout: post
title: Summary of GridapMakie.jl capabilities and end of GSoC 2021
---

Finally, two and a half after the beginning of GSoC 2021, we are almost ready to wrap up! Last week we introduced some important changes to our code, refactoring the way GridapMakie.jl calls the plotting functions. 
We were able to extend Makie's `plot`, `mesh`, `wireframe` and `scatter` to adapt them to Gridap's types `::Grid`, `::Triangulation` and `::CellField`. In this post I will show some results, all of them extracted
from the [README](https://github.com/gridap/GridapMakie.jl/blob/master/README.md) in GridapMakie.jl. There you will find additional information as well as a list of examples to be reproduced in your own computer!
In addition to that, this [Pull Request](https://github.com/gridap/GridapMakie.jl/pull/24) will contain a description of the project, which shall be provided to Google as the final evaluation report.

Let's get to some results! Since in [this post](https://paurierap.github.io/First-Plots/) we already saw some grid plots, we may as well try other things. For example, we can plot functions defined on the cells of a 2D triangulation:

<p align="center">
<img src="https://user-images.githubusercontent.com/64323465/130604754-b6bd0436-2a4a-40df-a156-daea685ceb0e.png" width="500"/>
</p>

or a function defined on the nodes of the boundary of such triangulation:

<p align="center">
<img src="https://user-images.githubusercontent.com/64323465/130608158-d4b00d8f-2ea1-40af-8bd0-9d81a040cba7.png" width="500"/>
</p>

Again, all the commands needed to plot these figures along a thorough description can be found on the README file. 

However, what we really want to see are the capabilities of GridapMakie.jl when having to plot more complex geometries. Let us take the geometry considered in the
[first Gridap tutorial](https://gridap.github.io/Tutorials/stable/pages/t001_poisson/#Tutorial-1:-Poisson-equation-1), so that we can plot it with the edges of the cells on the boundary:

<p align="center">
<img src="https://user-images.githubusercontent.com/64323465/130607389-e9c6c635-1a61-4192-a0fa-d14cb7fa80f7.png" width="500"/>
</p>

At this point, we may be convinced that GridapMakie.jl has been worth the effort and will prove to be quite useful and comfortable to all users, but that's not all! 
The package hides an ace up on its sleeve, since it can make use of Makie's [interactivity](http://makie.juliaplots.org/v0.15.1/documentation/nodes/index.html) and create observables that can be updated in real time. For example, we can record animations:
<p align="center">
<img src="https://user-images.githubusercontent.com/64323465/130611284-ade4326e-5491-42b3-b1fb-8a0671a9cb0a.gif" width="500"/>
</p>

Overall, even though it has many limitations, GridapMakie.jl steps up to be a clear alternative to using external software such as Paraview.
