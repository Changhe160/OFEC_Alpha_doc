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
class NSGAII
```

#### Member function

|Name|Utility|
|-|-|
|`survivor_selection(parent, offspring)`|Select the best half of `offspring` to replace `parent`|
|`nondominated_sorting(offspring)`|Use [fast nondominated sorting](../../../Utility/nondominated sorting/#fast-nondominated-sorting-fns) to sort `offspring`|
|`eval_dens(parent, offspring)`|Crowding and Replacement|

### NSGAII-SBX

#### Command line arguments example

`AN=NSGAII-SBX PS=100`

#### Class view

```c++
class NSGAII_SBX : public algorithm
```

#### Data member

|Name|Type|Utility|
|-|-|-|
|`m_pop`|`NSGAII_SBX_pop`||

#### Member function

|Name|Utility|
|-|-|
|`initialize()` &oplus;||
|`run_()` &oplus;||
|`record()` &oplus;||

#### Class view

```c++
class NSGAII_SBX_pop : public SBX_pop<>, NSGAII<individual<>>
```
Links: `SBX_pop` `NSGAII` `individual` 

#### Data member

|Name|Type|Utility|
|-|-|-|
|`m_offspring`|`vector<individual<>>`|Two size of `m_inds`, for the convenience of sorting and selecting|

#### Member function

|Name|Utility|
|-|-|
|`initialize()` &oplus;||
|`evolve()` &oplus;||
