---
title: MOEA-F
category: Instance
subcategory: problem
order: 23
---

#### Reference

H. Li and Q. Zhang
"Comparison Between NSGA-II and MOEA/D on a Set of Multiobjective Optimization Problems with Complicated Pareto Sets".
Technical Report CES-476, Department of Computer Science, University of Essex, 2007

#### Class view
```c++
class MOEA_FBase : public continuous
```
Link: [`continuous`](../continuous)

#### Member functions

|Name|Utility|
|-|-|
|`initialize()`||
|`evaluate_objective(x,obj)`||
|`LoadPF()`||
|`alphafunction(alpha,x,dim,type)`|Control the PF shape|
|`betafunction(x,type)`|Control the distance|
|`psfunc2(x,t1,dim,type,css)`|Control the PS shape of 2-d instances|
|`psfunc3(x,t1,t2,dim,type)`|Control the PS shapes of 3-D instances|

### MOEA-F1

#### String command example

`PN=MOP_MOEA_F1 ND=30` (`NO=2`)

#### Class view

```c++
class MOEA_F1 final : public MOEA_FBase
```

### MOEA-F2

#### String command example

`PN=MOP_MOEA_F2 ND=30` (`NO=2`)

#### Class view

```c++
class MOEA_F2 final : public MOEA_FBase
```

### MOEA-F3

#### String command example

`PN=MOP_MOEA_F3 ND=30` (`NO=2`)

#### Class view

```c++
class MOEA_F3 final : public MOEA_FBase
```

### MOEA-F4

#### String command example

`PN=MOP_MOEA_F4 ND=30` (`NO=2`)

#### Class view

```c++
class MOEA_F4 final : public MOEA_FBase
```

### MOEA-F5

#### String command example

`PN=MOP_MOEA_F5 ND=30` (`NO=2`)

#### Class view

```c++
class MOEA_F5 final : public MOEA_FBase
```

### MOEA-F6

#### String command example

`PN=MOP_MOEA_F6 ND=30` (`NO=3`)

#### Class view

```c++
class MOEA_F6 final : public MOEA_FBase
```

### MOEA-F7

#### String command example

`PN=MOP_MOEA_F7 ND=30` (`NO=2`)

#### Class view

```c++
class MOEA_F7 final : public MOEA_FBase
```

### MOEA-F8

#### String command example

`PN=MOP_MOEA_F8 ND=30` (`NO=2`)

#### Class view

```c++
class MOEA_F8 final : public MOEA_FBase
```

### MOEA-F9

#### String command example

`PN=MOP_MOEA_F9 ND=30` (`NO=2`)

#### Class view

```c++
class MOEA_F9 final : public MOEA_FBase
```