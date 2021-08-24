---
layout: post
title: Plotting of scalar fields on a grid
---

After a period of getting to know [Makie](https://github.com/JuliaPlots/Makie.jl) and trying to find the best approach for [Gridap](https://github.com/gridap) grids, we came up with a suitable way of plotting simplexified (i.e. made up by triangles) grids. 

Moreover, not only did we implement the recipes ```faces``` and ```edges``` but also ```vertices```, letting us plot something like
```julia
using Gridap, GridapMakie, GLMakie

# Create our square grid made up by triangles (or elements):
model = CartesianDiscreteModel((0,1,0,1),(5,5)) |> simplexify
grid = get_grid(model)

# Plot faces, edges and vertices:
fig = faces(grid, color=:lightseagreen, shading=true)
edges!(grid, color=:black, linestyle=:dash, linewidth=2.5)
vertices!(grid, color=:red, marker=:diamond, markersize=15)
fig
```
which will return the following figure

![Fig1](https://user-images.githubusercontent.com/64323465/127524921-31b18963-4e93-4bd6-bd1b-42d6459213a9.png)

We note here that ```faces``` returns a tuple of objects, those being a ```Figure``` and an ```Axis```. By making use of the former, we may plot several objects on top of each other, for example lines and dots over a painted surface. Such behaviour can be extended to 3D, like
```julia

# Create our square grid made up by triangles (or elements):
model = CartesianDiscreteModel((0,1,0,1,0,1),(1,1,1)) |> simplexify
grid = get_grid(model)

# Plot faces, edges and vertices:
fig = faces(grid, color=:lightseagreen, shading=true)
edges!(grid, color=:black)
vertices!(grid, color=:red)
fig
```
resulting in

![Fig1](https://user-images.githubusercontent.com/64323465/127526100-ee42a147-5317-4bcc-8885-ee8905e8422e.png)

Even though we already have implemented the use of colors to represent scalar nodal or cell fields, they are limited to simple arrays, e.g. ```nodaldata = rand(num_nodes(grid))``` in (note the use of a colorbar)
```julia
fig, _ , plt = faces(grid, color=nodaldata, colormap=:heat, colorrange=(0,1))
edges!(grid, color=:black)
Colorbar(fig[1,2], plt, ticks=0:0.25:1)
fig
```
seen as

![Fig3](https://user-images.githubusercontent.com/64323465/127527188-99ae2fb9-044f-4777-a3eb-5ea1446aca72.png)

Therefore, our next step is to adapt the solution representation to [Gridap](https://github.com/gridap) types.
