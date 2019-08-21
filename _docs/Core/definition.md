---
title: definition
category: Core
order: 1
---

#### Aliases

|Aliase|Orginal Type|
|-|-|
|``real``|``double`` or ``float``|
|``param_map``|``map<const string, typevar>``|

#### Enums

|Enum|Elements|
|-|-|
|``dominationship``|``Equal`` ``Dominating`` ``Dominated`` ``Non_dominated`` ``Non_comparable``|
|``optimization_mode``|``Minimization`` ``Maximization``|
|``caller``|``Problem`` ``Algorithm`` ``Demon``|
|``violation_type``|``Constraint`` ``Boundary`` ``None``|
|``constraint_type``|``Inequality`` ``Equality``|
|``evaluation_tag``|``Normal`` ``Change`` ``Terminate`` ``Change_next_eval`` ``Change_timelinkage`` ``Change_dimension`` ``Infeasible``|
|``problem_tag``|``null_tag`` ``SOP`` ``MOP`` ``DOP`` ``MMOP`` ``GOP`` ``ROOT`` ``ConOP`` ``ComOP`` ``TSP`` ``COP`` ``VRP`` ``TTP`` ``JSP`` ``KOP`` ``SAT`` ``ONEMAX`` ``QAP`` ``MKP`` ``EOP`` ``LSOP`` ``epanet``|

##### Problem tags

- `ConOP` continuous optimization problem
- `SOP` single objective problem
- `MOP` multi-objective problem
- `GOP` global optimization problem
- `MMOP` multi-modal optimization problem
- `COP` constraint optimization problem
- `DOP` dynamic optimization problem
- `EOP` expensive optimization problem
- `LSOP` large scale optimization problem
- `ROOT` robust optimzation problem

- `ComOP` combinatorial optimization problem
- `TSP` travelling salesman problem
- `VRP` vehicle routing problem
- `TTP` timetabling problem
- `JSP` job shop problem
- `KOP` knapsack optimization problem
- `SAT` boolean satisfiability problem
- `ONEMAX` one max problem
- `QAP` quadratic assignment problem
- `MKP` multi-dimensional knapsack problem