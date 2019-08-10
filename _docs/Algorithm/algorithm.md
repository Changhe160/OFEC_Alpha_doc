---
title: algorithm
category: Algorithm
order: 2
---

#### Class view

``class algorithm``

#### Data members

|Name|Type|Utility|
|-|-|-|
|``m_name``|``string``|The string command after ``AN=``|
|``m_term``|``unique_ptr<``[``termination``](../../Core/termination)``>``|The termination criterion|
|``m_parameters``|[``param_map``](../../Core/Aliases and Enums)|Parameters|

#### Major member functions

|Name|Utility|
|-|-|
|``initialize()``|The initialization process|
|``run_()``|The optimization process|
|``terminating()``|Return whether the termination criterion has been met|
|``record()``|Record informations for measurement|
