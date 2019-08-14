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
template <typename type_particle>
class swarm : public population<type_particle> 
```
Links: [`population`](../../../Core/algorithm/population)

#### Data members

|Name|Type|Utility|
|-|-|-|
|`m_C1` `m_C2`|`real`|The value of accelerators *C*$\_1$ and *C*$\_2$|
|`m_weight`|`real`|The value of inertia weight *W*|
|`m_link`|`vector<vector<bool>>`|The connected graph of particles|
|`m_flag_best_impr`|`bool`|Whether the global best particle improves|

#### Major member functions

|Name|Utility|
|-|-|
|`evolve()`||
|`set_neighborhood()`|The adaptive random topology by default|
|`get_best_neighbor(idx)`|Return the best neighbor of the `idx`-th particle|

### particle

#### Class view

```c++
class particle : public individual<> 
```
Links: [`individual`](../../../Core/algorithm/individual)

#### Data members

|Name|Type|Utility|
|-|-|-|
|`m_pbest`|`solution<>`|The personal best position|
|`m_vel`|`vector<real>`|The velocity vector|

#### Major member functions

|Name|Utility|
|-|-|
|`initialize_velocity()`||
|`next_velocity(lbest, w, c1, c2)`||
|`move()`||
|`clamp_velocity()`||

### SPSO-07

#### String command example

`AN=SPSO01 PS=100`

#### Reference

C. Maurice. (2007). ["Standard pso 2007 (spso-07)"](http://www.particleswarm.info/Programs.html).

#### Class view

```c++
class particle07 final : public particle
```

#### Overridden member functions

|Name|Utility|
|-|-|
|`initialize_velocity()`||
|`next_velocity(lbest, w, c1, c2)`||

#### Class view

```c++
class SPSO07 : public algorithm
```

#### String command example

`AN=SPSO01 PS=100`

#### Data member

|Name|Type|Utility|
|-|-|-|
|`m_pop`|`swarm<particle07>`||

#### Overridden member functions

|Name|Utility|
|-|-|
|`initialize()`||
|`run_()`||
|`record()`||

### SPSO-11

#### Reference

C. Maurice. (2011). ["Standard PSO 2011 (SPSO-2011)"](http://www.particleswarm.info/Programs.html).

#### Class view

```c++
class particle11 final : public particle
```

#### Overridden member functions

|Name|Utility|
|-|-|
|`initialize_velocity()`||
|`next_velocity(lbest, w, c1, c2)`||
|`clamp_velocity()`||

#### Class view

```c++
class SPSO11 : public algorithm
```

#### Data member

|Name|Type|Utility|
|-|-|-|
|`m_pop`|`swarm<particle11>`||

#### Overridden member functions

|Name|Utility|
|-|-|
|`initialize()`||
|`run_()`||
|`record()`||
