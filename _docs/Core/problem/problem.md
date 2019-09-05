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

#### Data member

|Name|Type|Utility|
|-|-|-|
|`m_name`|`string`|Name in command line arguments|
|`m_tag`|`set<problem_tag>`|[Tags](../../definition#problem-tags) of the problem|
|`m_variable_size`|`size_t`|Size of decision variables|
|`m_objective_size`|`size_t`|Number of objectives|
|`m_opt_mode`|`vector<optimization_mode>`|Optimization mode of each objective value|
|`m_constraint_type`|`vector<constraint_type>`|Types of each constraint|
|`m_effective_eval`|`size_t`|How many solutions the ***algorithm*** evaluates|
|`m_objective_accuracy`|`real`|The minimum distance to tell apart two different objective values|

#### Member function

|Name|Utility|
|-|-|
|`initialize()` &empty;|Initialize problem infos|
|`initialize_solution(s)` &empty;|Default initilization for solution|
|`evaluate_(s, ...)` &empty;|How to evaluate a given solution `s`|
|`variable_distance(s1, s2)` &empty;|Return the distance between soluions `s1` and `s2` in decision space|
|`variable_distance(x1, x2)` &empty;|Return the distance between decision variables `x1` and `x2`|
|`same(s1, s2)` &empty;|Return whether `s1` and `s2` are the same solution|