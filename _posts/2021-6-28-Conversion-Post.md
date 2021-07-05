---
layout: post
title: First steps of the project
---

During these first weeks, we have been looking at the type conversions provided by [Makie](https://github.com/JuliaPlots/Makie.jl). By doing so, we don't need to create our own plotting functions from scratch, but rather extend the existing ones for the kind of objects that [Gridap](https://github.com/gridap) considers. 

We are now focused on the graphing of computational grids, either in 1D, 2D or 3D. For example, if one creates the 2D grid:
```julia
model = CartesianDiscreteModel((0.,1.5,0.,1.),(15,10)) |> simplexify
grid = get_grid(model)
```
it is possible to plot the faces using ```mesh(grid)``` or even ```wireframe(grid)``` to see the edges of the elements. These simple conversions will walk us to the next step, the creation of the recipes, i.e. plotting commands along with its plotting types, ```edges``` and ```faces```. These two will improve the capabilities of the conversion, allowing to draw every type of element (triangles and quadrilaterals), as well as cell and nodal fields.

For the next post, we hope to provide proof of the working recipes to visualize a wide range of grids in any dimension. 
