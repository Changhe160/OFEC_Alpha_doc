---
title: continuous
category: Core
subcategory: problem
order: 4
---

#### Class view
```c++
class continuous : public problem
```
Link: [`problem`](../problem)

#### Data member

|Name|Type|Utility|
|-|-|-|
|`m_domain`|[`domain`](../domain)|Range of each decision variable|
|`m_init_domain`|[`domain`](../domain)|Some benchmarks limit the domain for initial solutions (e.g. [CEC2005-F25](../../../Instance/problem/CEC2005-GOP/#f25))|
|`m_variable_accuracy`|`real`|The minimum distance to distinguish two different decision variables|
|``|||

#### Member function

|Name|Utility|
|-|-|
|`evaluate_objective(x, obj`||
