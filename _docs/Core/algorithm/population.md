---
title: population
category: Core
subcategory: algorithm
order: 6 
---

> The population is defined as a class template to support member individuals of different variable or objective encoding. 

#### Class view

```c++
template<typename Individual>
class population
```

#### Data members

|Name|Type|Utility|
|-|-|-|
|`m_inds`|`vector<unique_ptr<Individual>>`|Member individuals of the current population|
|`m_iter`|`size_t`|The current number of iterations|
|`m_id`|`int`|The index number in the multi-population|
|`m_best`|`vector<unique_ptr<Individual>>`|Best individuals found so far|
|`m_worst`|`vector<unique_ptr<Individual>>`|Worst individuals found so far|

>In multi-modal or multi-objective optimization, there may be more than one best and worst individuals.

#### Major member functions

|Name|Utility|
|-|-|
|`initialize()`|Initialize `m_inds`|
|`evluate()`|Evaluate `m_inds`|
|`evolve()`|Optimization operations in each iteration|
|`update_best()`|Update `m_best`|
|`update_worst()`|Update `m_worst`|
|`update_best(s)`|Update `m_best` according to the given solution `s`|
|`update_worst(s)`|Update `m_worst` according to the given solution `s`|
