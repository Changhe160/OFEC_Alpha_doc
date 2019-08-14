---
title: One Max
category: Instance
subcategory: problem
order: 51
---

#### Class view

```c++
class one_max : public problem
```
Link: [`problem`](../problem)

#### Added data members

|Name|Type|Utility|
|-|-|-|
|`m_optima`|`optima<variable_vector<int>, real>`|The global optima|
|`m_if_valid_check`|`bool`|Whether or not the validation check is necessary|

#### Major member functions

|Name|Utiliy|
|-|-|
|`initialize()`|Initialize `m_optima` and [`m_opt_mode`](../problem/#major-data-members)|
|`evaluate_(s, ...)`|How to evaluate the solution `s`|
|`initialize_solution(s)`|How to initialize the solution `s`|
|`variable_distance(s1, s2)`|Return the distance in decision space between solutions `s1` and `s2`|
|`is_valid(s)`|Check and return whether or not the solution `s` is valid|