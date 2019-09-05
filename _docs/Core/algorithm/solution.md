---
title: solution
category: Core
subcategory: algorithm
order: 4
---

#### Class view

```c++
template<typename VariableEncoding = variable_vector<real>, 
         typename ObjetiveType = real>
class solution : public solution_base
```
Link: [`real`](../../definition#aliases) [`variable_vector`](../encoding#variable-vector)

#### Data member

|Name|Type|Utility|
|-|-|-|
|`m_var`|`VariableEncoding`|Decision variables|
|`m_obj`|`vector<ObjectiveType>`|Objective values|
|`m_constraint_value`|`vector<`[`real`](../../definition)`>`|The constraint violation|

#### Member function

|Name|Utility|
|-|-|
|`initialize()`|Call the problem instance to initialize the decision variables|
|`evaluate(effective=true, caller=caller:Algorithm)`|Call the problem instance to calculate the objective values and the constraint violation|
|`dominate(s)`|Return whether or not the solution dominates the passed solution|