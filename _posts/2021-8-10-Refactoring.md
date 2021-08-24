---
layout: post
title: Refactoring
---

Change of plans! We decided that the recipes we were using (those being `cells`, `edges` and `vertices`) were too confusing for a user, given the frequency those names appear in common finite element scripts. Therefore, we agreed on just extending existing Makie functions to do the work the previous recipes were supposed to: `mesh` will cover for `cells`, `wireframe` will substitute `edges` and the same for `scatter` and `vertices`. This way, we make sure that any user being familiar with Makie is able to replicate those functions with Gridap types.

Additionally, this refactoring will allow for interactive plots, a feature with endless possibilities! This post is a brief one but will be followed by a big post containing all the capabilites of GridapMakie, just before GSoC 2021 ends and we register the package on the Julia official Registry.
