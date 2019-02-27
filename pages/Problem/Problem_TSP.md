---
title: TSP
last_updated: Feb 27, 2019 by Junchen Wang
sidebar: API_sidebar
permalink: Problem_TSP.html
folder: Problem
---

## Class Inheritance

[`problem`][Problem_problem] &larr; `travelling_salesman`

## Description

The example of command arguments is shown as below:
```
PN=TSP NO=1 DF1=A280
```

## Data Members

|Name|Information|
|-|-|
|**mvvv_cost**|A 3-D matrix representing the cost between cities, where `mvvv_cost[i][j][k]` denotes the cost between city`j` and city`k` on the `i`-th objective.|
|**m_file_name**|Name of the tsp data file, e.g., `A280`.|
|**m_domain**|Boundary of each variable, usually is between `[0 : N-1]`, where `N` denotes the total number of cities.|
|**m_optima**|The optimal traversal sequence of cities, which is obtained from the file "./data/[tsp date file name].opt.tour".|
|**mvv_nearby**|A 2-D matrix representing the nearby cities of each city, where `mvv_nearby[i][j]` denotes the `j+1` nearest city of city`i`. It is empty before calling `find_nearby_city()`.|


## Member Functions

{% include links.html %}