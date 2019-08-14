---
title: algorithm
category: Core
subcategory: algorithm
order: 1
---

#### Class view

``class algorithm``

#### Data members

|Name|Type|Utility|
|-|-|-|
|``m_name``|``string``|The string command after ``AN=``|
|``m_term``|``unique_ptr<``[``termination``](../../Core/termination)``>``|The termination criterion|
|``m_parameters``|[``param_map``](../../Core/definition)|Parameters|

#### Major member functions

|Name|Utility|
|-|-|
|``initialize()``|The initialization process|
|``run_()``|The optimization process|
|``terminating()``|Return whether the termination criterion has been met|
|``record()``|Record informations for measurement|
