---
title: solution
category: Core
subcategory: algorithm
order: 4
---

> The solution in OFEC is defined as a class template to support solution representation in both continuous and combinatorial space or using hybrid encoding schemes.

#### Class view

```c++
template<typename variable_encoding = variable_vector<real>, objetive_type = real>
class solution : public solution_base
```

- The 1st template parameter `variable_encoding` determines the representaion of the solution's decision variables
- The 2nd template parameter `objetive_type` determines the type of the solution's objective values.

#### Data members

|Name|Type|Utility|
|-|-|-|
|`m_var`|`variable_encoding`|Decision variables|
|`m_obj`|`vector<objective_type>`|Objective values|
|`m_constraint_value`|`vector<`[`real`](../../Core/Aliases and Enums)`>`|The constraint violation|

#### Major member functions

|Name|Utility|
|-|-|
|`initialize()`|Call the problem instance to initialize its decision variables|
|`evaluate(effective=ture,caller=algorithm)`|Call the problem object to calculate its objective values and constraint violation|
|`dominate(s)`|Return whether or not the solution dominates a given solution `s`|

>The comparison is based on the objective values and the problem optimization mode (to minimize or maximize each objective).