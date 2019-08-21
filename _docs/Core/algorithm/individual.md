---
title: individual
category: Core
subcategory: algorithm
order: 5
---

#### Class view

```c++
template<typename variable_encoding = variable_vector<real>, objetive_type = real>
class individual : public solution<variable_encoding, objetive_type>
```
Link: [`solution`](../solution) `variable_vector`

#### Added data members

|Name|Type|Utility|
|-|-|-|
|`m_fitness`|`real`|The fitness value|
|`m_id`|`int`|The index number in the population|
|`m_rankding`|`int`|The rank number in the population|
|`m_improved`|`bool`|Whether or not is improved in the last evoluation|
|`m_active`|`bool`|Whether or not takes part in the next evolution|