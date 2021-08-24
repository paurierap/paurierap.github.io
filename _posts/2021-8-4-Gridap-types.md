---
layout: post
title: Inclusion of Gridap function types to plotting
---

This time, the blog post needed to be delayed for a week after a harsh and unpleasant encounter with COVID-19. Fortunately, I feel completely recovered and the project is on track once again. From now on, we will be working on [this issue](https://github.com/gridap/GridapMakie.jl/issues/21),
where we further adapt GridapMakie.jl to account for more Gridap types: more precisely, the `::Triangulation` and `::CellField` types. Moreover, we shall extend the function `plot` provided by Makie to be an alias of `cells(::Triangulation)`or `cells(::CellField)`. This way, 
we can have the following triangulations
```julia

using Gridap, GridapMakie, GLMakie

domain = (0,1,0,1)
cell_nums = (10,10)

# Create 2D model of a grid:
model = CartesianDiscreteModel(domain,cell_nums) |> simplexify
Ω = Triangulation(model) # Extract triangulation.
Γ = BoundaryTriangulation(model) # Extract boundary triangulation, i.e., the outermost borders.
Λ = SkeletonTriangulation(model) # Extract skeleton triangulation, i.e., the inner borders.
uh = CellField(x->x[1]+x[2],Ω) # Create a function defined on the nodes of Ω.
cell_to_val = rand(num_cells(Ω)) # Random field defined on the cells.
```
and plot them like
```julia

cells(Ω,color=:green) # Plot (or mesh) Ω with a green color.
cells(Ω,color=uh) # Plot (or mesh) Ω with the nodal field uh.
plot(Ω,uh) # == cells(Ω,color=uh)
plot(uh) # alias for: plot(get_triangulation(uh),uh)
cells(Ω,color=cell_to_val) # Plot (or mesh) Ω with the cell field cell_to_val.

# Plot the boundaries of the cells of Ω:
edges(Ω) 
edges(Ω,color=:green)
```

In order to convert any `::Triangulation` and `::CellField` to plottable grids and arrays of colors, we shall use `Gridap.Visualization`, a conveniently built tool that will allow to extract the suitable data.
