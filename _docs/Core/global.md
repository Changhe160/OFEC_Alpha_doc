---
title: global
category: Core
order: 1
---

>In OFEC, all instances involved in a run are mananged by a `global` instance.

#### Class view

```c++
struct global
```
#### Major data members

|Name|Type|Utility|
|-|-|-|
|`m_problem`|`unique_ptr<problem>`|The problem instance|
|`m_algorithm`|`unique_ptr<algorithm>`|The algorithm instance|
|`m_uniform`|`map<caller,unique_ptr<uniform>>`|Uniform random generators|
|`m_normal`|`map<caller,unique_ptr<normal>>`|Normal random generators|
|`m_cauchy`|`map<caller,unique_ptr<cauchy>>`|Cauchy random generators|
|`m_levy`|`map<caller,unique_ptr<levy>>`|Levy random generators|
|`m_gammma`|`map<caller,unique_ptr<gammma>>`|Gamma random generators|

#### Static data member

|Name|Type|Utility|
|-|-|-|
|`ms_global`|`shared_ptr<global>`|The only access to the global instance|

#### Examples

`global::ms_global->m_problem`:

`global::ms_global->m_algorithm`:

`global::ms_global->m_uniform[caller::Algorithm]`:

`global::ms_global->m_normal[caller::Problem]`: