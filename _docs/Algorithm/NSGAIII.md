---
title: NSGA-III
category: Algorithm
order: 11
---

#### Reference

[K. Deb and H. Jain. (2014).
"An Evolutionary Many-Objective Optimization Algorithm Using Reference-Point-Based Nondominated Sorting Approach, Part I: Solving Problems With Box Constraints,"
*IEEE Transactions on Evolutionary Computation*. 18 (4): 577-601.](https://doi.org/10.1109/TEVC.2013.2281535)

#### Class view

```c++
template<typename Individual>
class NSGAIII : public population<Individual> 
```
Links: [``population``](../../Core/population)

#### Data members

|Name|Type|Utility|
|-|-|-|
|``m_offspring``|``vector<Individual>``|Two size of ``m_pop``, for the convenience of sorting and selecting|
|``mv_rps``|``vector<``[``ref_point``](#reference-point)``>``|Reference points|
|``mv_obj_division_p_``|``vector<size_t>``||
|``mvv_off_conv_obj``||

#### Major member functions

|Name|Utility|
|-|-|
|``evolve()``|Optimization operators in each iteration|
|``evolve_mo()``|Reproduction process (pure virtual function here)|
|``sort()``|Fast nondominated sorting process|
|``environmental_selection()``|Survivor selection process|

### Reference point

#### Class view
```c++
class ref_point
```

#### Data members

|Name|Type|Utility|
|-|-|-|
||||

#### Major member functions

|Name|Utility|
|-|-|
|||

### NSGAIII-SBXRM

#### Class view

```c++
class NSGAIII_SBXRM_pop : public NSGAIII<individual<>>, SBX_RealMutate
```
Links: `NSGAIII` `individual` `NSGAIII`