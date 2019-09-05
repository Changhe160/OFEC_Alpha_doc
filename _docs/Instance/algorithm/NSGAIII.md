---
title: NSGA-III
category: Instance
subcategory: algorithm
order: 11
---

#### Reference

[K. Deb and H. Jain. (2014).
"An Evolutionary Many-Objective Optimization Algorithm Using Reference-Point-Based Nondominated Sorting Approach, Part I: Solving Problems With Box Constraints,"
*IEEE Transactions on Evolutionary Computation*. 18 (4): 577-601.](https://doi.org/10.1109/TEVC.2013.2281535)

#### Class view

```c++
template<typename Individual>
class NSGAIII
```

#### Data member

|Name|Type|Utility|
|-|-|-|
|`mv_rps`|`vector<`[`ref_point`](#reference-point)`>`|Reference points|
|`mv_obj_division_p_`|`vector<size_t>`||
|`mvv_off_conv_obj`|`vector<vector<real>>`||

#### Member function

|Name|Utility|
|-|-|
|`survivor_selection(parent, offspring)`|Reproduction process (pure virtual function here)|
|`nondominated_sorting(offspring)`|Fast nondominated sorting process|

### Reference point

#### Class view
```c++
class ref_point
```

#### Data member

|Name|Type|Utility|
|-|-|-|
||||

#### Member function

|Name|Utility|
|-|-|
|||

### NSGAIII-SBX

#### Command line arguments example

`AN=NSGAII-SBX PS=100`

#### Class view

```c++
class NSGAIII_SBX : public algorithm
```

#### Data member

|Name|Utility|
|-|-|
|`m_pop`|`NSGAIII_SBX_pop`|

#### Member function

|Name|Utility|
|-|-|
|||

#### Class view

```c++
class NSGAIII_SBX_pop : public SBX_pop<>, NSGAIII<individual<>>
```
Links: `SBX_pop` `NSGAIII` `individual`

#### Data member

|Name|Type|Utility|
|-|-|-|
|`m_offspring`|`vector<individual<>>`|Two size of `m_inds`, for the convenience of sorting and selecting|

#### Member function

|Name|Utility|
|-|-|
|||

