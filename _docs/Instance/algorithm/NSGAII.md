---
title: NSGA-II
category: Instance
subcategory: algorithm
order: 10
---

#### Reference

[Kalyanmoy Deb, Amrit Pratap, Sameer Agarwal, and T.Meyarivan. (2002).
A Fast and Elitist Multiobjective Genetic Algorithm : NSGA-II.
*IEEE Transactions on Evolutionary Compuation*. 6 (2): 182 - 197.](https://doi.org/10.1109/4235.996017)

#### Class view

```c++
template<typename Individual>
class NSGAII : public population<Individual>
```
Links: [`population`](../../Core/population)

#### Data members

|Name|Type|Utility|
|-|-|-|
|`m_offspring`|`vector<Individual>`|Two size of `m_pop`, for the convenience of sorting and selecting|

#### Major member functions

|Name|Utility|
|-|-|
|`evolve()`|Optimization operators in each iteration|
|`evolve_mo()`|Reproduction process (pure virtual function here)|
|`sort()`|Use [fast nondominated sorting](../../Utility/nondominated sorting/#fast-nondominated-sorting-fns) to sort `m_offspring`|
|`eval_dens()`|Survivor selection process|

### NSGAII-SBXRM

#### Class view

```c++
class NSGAII_SBXRM : public NSGAII<individual<>>, SBX_RealMutate
```
Links: `NSGAII` `individual<>` `SBX_RealMutate`