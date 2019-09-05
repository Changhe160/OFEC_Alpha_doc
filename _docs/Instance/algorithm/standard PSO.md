---
title: Standard PSO
category: Instance
subcategory: algorithm
order: 3
---

#### Reference

[R. Eberhart and J. Kennedy. (1995).
"A new optimizer using particle swarm theory".
*Proceedings of the Sixth International Symposium on Micro Machine and Human Science*.](https://doi.org/10.1109/MHS.1995.494215)

#### Pseudocode

1. Set algorithm parameters *C*$\_1$, *C*$\_2$, and *W*
1. Initialize swarm $\mathbb{S}=\\{\mathbf{p}_1,\ldots,\mathbf{p}_N\\}$.
	1. For each $\mathbf{p}_i \in \mathbb{S}$:
		1. Initialize $\mathbf{p}_i=\\{$***x***, ***v***, ***x***$\_{pbest}$, *f*(***x***), *f*(***x***$\_{pbest}$)$\\}$
		1. Evaluate *f*(***x***)
		1. $\\{$***x***$\_{pbest}$, *f*(***x***$\_{pbest}$)$\\}\gets\\{$ ***x***, *f*(***x***)$\\}$
	1. [*update_best*](../../../Core/algorithm/population/#major-member-functions)()
1. While *termination criterion* is not fulfilled:
	1. For each $\mathbf{p}_i\in \mathbb{P}$ (with random sequence):
		1. *set_neighborhood*()
		1.  $\\{$***x***$\_{lbest}$, *f*(***x***$\_{lbest}$)$\\}\gets$ *get_best_neighbor*($i$)
		1. ***v*** $\gets$ *next_velocity*(***x***$\_{lbest}$, *W*, *C*$\_1$, *C*$\_2$)
		1. ***x*** $\gets$ *move*(***x***, ***v***)
		1. ***x*** $\gets$ *clamp_velocity*(***x***)
		1. Evaluate *f*(***u***)
		1. If *better*(*f*(***x***), *f*(***x***$\_{pbest}$)):
			1. $\\{$***x***$\_{pbest}$, *f*(***x***$\_{pbest}$) $\\}\gets\\{$***x***, *f*(***x***)$\\}$
			1. [*update_best*](../../../Core/algorithm/population/#major-member-functions)($\\{$***x***, *f*(***x***)$\\}$)
1. Output results

### swarm

#### Class view

```c++
template <typename Particle>
class swarm : public population<Particle> 
```
Links: [`population`](../../../Core/algorithm/population)

#### Data member

|Name|Type|Utility|
|-|-|-|
|`m_C1` `m_C2`|`real`|The value of accelerators *C*$\_1$ and *C*$\_2$|
|`m_weight`|`real`|The value of inertia weight *W*|
|`m_link`|`vector<vector<bool>>`|The connections between particles|
|`m_flag_best_impr`|`bool`|Whether the global best particle improves|

#### Member function

|Name|Utility|
|-|-|
|`evolve()` &oplus;||
|`set_neighborhood()`|The adaptive random topology by default|
|`get_best_neighbor(idx)`|Return the best neighbor of the `idx`-th particle|

### particle

#### Class view

```c++
class particle : public individual<> 
```
Links: [`individual`](../../../Core/algorithm/individual)

#### Data member

|Name|Type|Utility|
|-|-|-|
|`m_pbest`|`solution<>`|The personal best position|
|`m_vel`|`vector<real>`|The velocity vector|

#### Member function

|Name|Utility|
|-|-|
|`initialize_velocity()`||
|`next_velocity(lbest, w, c1, c2)`||
|`move()`||
|`clamp_velocity()`||

### SPSO-07

#### Reference

C. Maurice. (2007). ["Standard pso 2007 (spso-07)"](http://www.particleswarm.info/Programs.html).

#### Command line arguments example

`AN=SPSO07 PS=100`

#### Class view

```c++
class SPSO07 final : public algorithm
```

#### Data member

|Name|Type|Utility|
|-|-|-|
|`m_pop`|`swarm<particle07>`||

#### Member function

|Name|Utility|
|-|-|
|`initialize()` &oplus;||
|`run_()` &oplus;||
|`record()` &oplus;||

#### Class view

```c++
class particle07 final : public particle
```

#### Member function

|Name|Utility|
|-|-|
|`initialize_velocity()` &oplus;||
|`next_velocity(lbest, w, c1, c2)` &oplus;||

### SPSO-11

#### Reference

C. Maurice. (2011). ["Standard PSO 2011 (SPSO-2011)"](http://www.particleswarm.info/Programs.html).

#### Command line arguments example

`AN=SPSO11 PS=100`

#### Class view

```c++
class SPSO11 final : public algorithm {
```

#### Data member

|Name|Type|Utility|
|-|-|-|
|`m_pop`|`swarm<particle11>`||

#### Member function

|Name|Utility|
|-|-|
|`initialize()` &oplus;||
|`run_()` &oplus;||
|`record()` &oplus;||

#### Class view

```c++
class particle11 final : public particle
```

#### Member function

|Name|Utility|
|-|-|
|`initialize_velocity()` &oplus;||
|`next_velocity(lbest, w, c1, c2)` &oplus;||
|`clamp_velocity()` &oplus;||