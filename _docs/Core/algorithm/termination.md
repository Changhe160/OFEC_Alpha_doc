---
title: termination
category: Core
subcategory: algorithm
order: 2
---

> The termination instance also calculates the runtime of algorithm. The timer starts when the termination instance is constructed. 

#### Class view

```c++
class termination
```

#### Data members

|Name|Type|Utility|
|-|-|-|
|``m_start_time``, ``m_end_time``|[``time_point<systemclock>``](https://en.cppreference.com/w/cpp/chrono/time_point)|The start time and end time|
|``m_enable``|``bool``|Whether or not the criterion is enaled|
|``m_is_terminated``|``bool``|Whether or not the algorithm has been terminated|

#### Major Member functions

|Name|Utility|
|-|-|
|``terminating()``|Return whether or not the **global optima have been found** or the maximum runtime has been reached|
|``set_terminated_true()``|Mark the end of the algorithm and Terminate the timer|
|``duration()``|Return the runtime so far|

### term_max_iteration

#### Class view

```c++
class term_max_iteration : public termination
```

#### Added data members

|Name|Type|Utility|
|-|-|-|
|``m_max_iter``|``int``|The maximum number of iterations|

#### Added member functions

|Name|Utility|
|-|-|
|``terminating(num_iter)``|Return whether or not the **maximum number of iterations has been reached**|

### term_max_evals

#### Class view

```c++
class term_max_evals : public termination
```

#### Added data members

|Name|Type|Utility|
|-|-|-|
|``m_max_evals``|``int``|The maximum number of evalutations|

#### Added member functions

|Name|Utility|
|-|-|
|``terminating(num_evals)``|Return whether or not the **maximum number of evalutations has been reached**|

### term_best_remain

#### Class view

```c++
class term_best_remain : public termination
```

#### Added data members

|Name|Type|Utility|
|-|-|-|
|``m_max_iter``|``int``|The maximum number of successive iterations over which the best solution remains|
|``m_suc_iter``|``int``|The number of successive iterations over which the best solution remains|
|``m_previous``,``m_current``|``real``|The objective values of the previous and current best solution|

#### Added member functions

|Name|Utility|
|-|-|
|``terminating(current_best)``|Return whether or not the **maximum number of successive iterations over which the best solution remains has been reached**|