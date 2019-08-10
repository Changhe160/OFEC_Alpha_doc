---
title: Canonical DE
category: Algorithm
order: 4
---

#### Reference

[R. Storn, and K. Price. (1997).
"Differential Evolution - A Simple and Efficient Heuristic for Global Optimization over Continuous Spaces".
*Journal of Global Optimization*. 11: 341-359.](https://doi.org/10.1023/A:1008202821328)

#### Pseudocode

1. Set algorithm parameters *F*, *CR*, mutation strategy, and recombination strategy
1. Initialize population $\mathbb{P}=\\{\mathbf{p}_1,\ldots,\mathbf{p}_N\\}$.
	1. For each $\mathbf{p} \in \mathbb{P}$:
		1. Initialize $\mathbf{p}=\\{$***x***, ***v***, ***u***, *f*(***x***)$\\}$
		1. Evaluate *f*(***x***)
1. While *termination criterion* is not fulfilled:
	1. For each $\mathbf{p} \in \mathbb{P}$:
		1. ***v*** $\gets$ *mutate*(*F*, ***x***$\_{r_1}$, ***x***$\_{r_2}$, ***x***$\_{r_3}$, ...)
		1. ***u*** $\gets$ *recombine*(*CR*, ***x***, ***v***)
		1. Evaluate *f*(***u***)
		1. ***x*** $\gets$ *select*(***x***, *f*(***x***), ***u***, *f*(***u***))
1. Output results

#### Class view 

```c++
class Canonical_DE : public algorithm
```
Link: [`algorithm`](../algorithm)

#### Data members

|Name|Type|Utility|
|-|-|-|
|`m_pop`|[`DE::population`](#depopulation)`<`[`DE::individual`](#deindividual)`>>`|The population|

#### Major member functions

|Name|Utility|
|-|-|
|`intialize()`|Set parameters; initialize and evaluate the population (Pseudocode 1., 2.) |
|`run_()`|The optimization process (Pseudocode 3.)|
|`record()`|Record the evluations and the error in GOPs. Record the evaluations and the number of optima found in MMOPs.|

### DE::population

#### Class view 

```c++
template<typename Individual>
class DE::population : public population<Individual>
```
Links: [`population`](../../Core/population)

#### Data members

|Name|Type|Utility|
|-|-|-|
|`m_F`|`real`|The value of parameter *F*|
|`m_CR`|`real`|The value of parameter *CR*|

#### Major member functions

|Name|Utility|
|-|-|
|`evolve()`|Optimization operators in each iteration (Pseudocode 3.1.)|

### DE::individual

#### Class view 

```c++
class DE::individual : public individual<variable_vector<real>, real>
```
Links: [`individual`](../../Core/individual)

#### Data members

|Name|Type|Utility|
|-|-|-|
|`m_pv`|`solution<>`|The donor vector|
|`m_pu`|`solution<>`|The trial vector|

#### Major member functions

|Name|Utility|
|-|-|
|`mutate(F, r1, r2, r3, r4, r5)`|Pseudocode 3.1.1.|
|`recombine(CR, rs)`|Pseudocode 3.1.2.|
|`select()`|Pseudocode 3.1.4.|

### DE/rand/1

#### String command example

`AN=DE-rand-1 PS=100`

#### Mutation strategy

***v*** = ***x***$\_{r_1}$ + ***F*** $\cdot$ (***x***$\_{r_2}$ - ***x***$\_{r_3}$) 

#### Class view

```c++
class DE_rand_1 : public Canonical_DE
```

#### Overridden member function

|Name|Utility|
|-|-|
|`initialize()`|Set the mutation strategy to `DE::mutation_strategy::rand_1`|

### DE/best/2

#### String command example

`AN=DE-best-2 PS=100`

#### Mutation strategy

***v*** = ***x***$\_{best}$ + ***F*** $\cdot$ (***x***$\_{r_1}$ - ***x***$\_{r_2}$) + ***F*** $\cdot$ (***x***$\_{r_3}$ - ***x***$\_{r_4}$)

#### Class view

```c++
class DE_best_2 : public Canonical_DE
```

#### Overridden member function

|Name|Utility|
|-|-|
|`initialize()`|Set the mutation strategy to `DE::mutation_strategy::best_2`|

### DE/nrand/1

#### String command example

`AN=DE-nrand-1 PS=100`

#### Reference

[Michael G. Epitropakis, Vassilis P. Plagianakos, and Michael N. Vrahatis. (2011).
"Finding multiple global optima exploiting differential evolution’s niching capability".
*IEEE Symposium on Differential Evolution (SDE)*](https://doi.org/10.1109/SDE.2011.5952058)

#### Mutation strategy

***v*** = ***x***$\_{nearest}$ + ***F*** $\cdot$ (***x***$\_{r_1}$ - ***x***$\_{r_2}$)

#### Class view

```c++
class DE_nrand_1 : public Canonical_DE
```

#### Overridden member function

|Name|Utility|
|-|-|
|`initialize()`|Set the mutation strategy to `DE::mutation_strategy::nrand_1`|

