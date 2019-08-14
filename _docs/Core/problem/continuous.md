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

#### Data members

|Name|Type|Utility|
|-|-|-|
|`m_domain`|[`domain`](../../Core/domain)|Range of each decision variable|
|`m_init_domain`|[`domain`](../../Core/domain)|Some benchmarks limit the domain for initial solutions (e.g. [CEC2005-F25](../CEC2005-GOP/#f25))|
|`m_variable_accuracy`|`real`|The minimum distance to distinguish two different decision variables|
|``|||
