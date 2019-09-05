---
title: encoding
category: Core
subcategory: algorithm
order: 3
---

### Variable vector

#### Class view

```c++
template<typename VariableType>
class variable_vector : public variable_base
```

#### Data member

|Name|Type|Utility|
|-|-|-|
|`m_x`|`vector<VariableType>`||

#### Member function

|Name|Utility|
|-|-|
|`vect()`|Return `m_x`|

### Class view
```c++
class variable_base {
public:
    virtual ~variable_base() = default;
};
```

### Solution base

#### Class view

```c++
class solution_base {
public:
    virtual evaluation_tag evaluate(bool=true, caller= caller::Algorithm) = 0;
    virtual ~solution_base() {};
    solution_base(const solution_base&) = default;
    solution_base(solution_base&&) = default;
    solution_base() = default;
    solution_base& operator=(const solution_base&) = default;
    solution_base& operator=(solution_base&&) = default;
};
```