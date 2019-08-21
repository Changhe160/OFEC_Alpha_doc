---
title: problem
category: Core
subcategory: problem
order: 1
---

#### Class view
```c++
class problem
```

#### Major data members

|Name|Type|Utility|
|-|-|-|
|`m_name`|`string`|String command|
|`m_tag`|`set<problem_tag>`||
|`m_variable_size`|`size_t`||
|`m_objective_size`|`size_t`||
|`m_opt_mode`|`vector<optimization_mode>`|Optimization mode of each objective value|
|`m_constraint_type`|`vector<constraint_type>`|
|`m_effective_eval`|`size_t`|How many solutions the **algorithm** evaluates|
|`m_objective_accuracy`|`real`|The minimum distance to distinguish two different objective values|

#### Frequently-used member functions

|Name|Utility|
|-|-|
|`initialize()`|Initilize necessary data members (e.g., `m_domain`, `m_optima`)|
|`variable_size()`||
|`objective_size()`||
|`opt_mode(i)`|Return the optimization mode of the i-th objective|
|`has_tag(tag)`||
|`evluations()`|Return `m_effective_eval`|
|`evaluate(s, ...)`|Record some statistics and call `evaluate_(s, ...)`|
|`evaluate_(s, ...)`|How to evaluate the given solution `s`|