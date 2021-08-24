---
layout: post
title: Summary of GridapMakie.jl capabilities and end of GSoC 2021
---

Finally, two and a half after the beginning of GSoC 2021, we are almost ready to wrap up! Last week we introduced some important changes to our code, refactoring the way GridapMakie.jl calls the plotting functions. 
We were able to extend Makie's `plot`, `mesh`, `wireframe` and `scatter` to adapt them to Gridap's types `::Grid`, `::Triangulation` and `::CellField`. In this post I will show some results, all of them extracted
from the [README](https://github.com/gridap/GridapMakie.jl/blob/master/README.md) in GridapMakie.jl. There you will find additional information as well as a list of examples to be reproduced in your own computer!
In addition to that, this [Pull Request](https://github.com/gridap/GridapMakie.jl/pull/24) will contain a description of the project, which shall be provided to Google as the final evaluation report.

Let's get to some results! Since 
