---
title: DTLZ
category: Problem
order: 31
---

#### Reference

Deb, K., Thiele, L., Laumanns, M., & Zitzler, E. (2005). 
"Scalable test problems for evolutionary multiobjective optimization". 
In*Evolutionary multiobjective optimization* (pp. 105-145). Springer London.

#### Class view
```c++
class DTLZ : public continuous
```
Link: [`continuous`](../continuous)

#### Member functions

|Name|Utility|
|-|-|
|`initialize()`||
|`LoadPF()`||
|`generate_PF()`||

### MOEA-F1

#### String command example

`PN=MOP_DTLZ1 IT=5 NO=3` (`ND=NO-1+IT`)

#### Class view

```c++
class DTLZ1 final : public DTLZ
```

### MOEA-F2

#### String command example

`PN=MOP_DTLZ2 IT=10 NO=3` (`ND=NO-1+IT`)

#### Class view

```c++
class DTLZ2 final : public DTLZ
```

### MOEA-F3

#### String command example

`PN=MOP_DTLZ3 IT=10 NO=3` (`ND=NO-1+IT`)

#### Class view

```c++
class DTLZ3 final : public DTLZ
```

### MOEA-F4

#### String command example

`PN=MOP_DTLZ4 IT=5 NO=3` (`ND=NO-1+IT`)

#### Class view

```c++
class DTLZ4 final : public DTLZ
```

### MOEA-F6

#### String command example

`PN=MOP_DTLZ6 IT=20 NO=3` (`ND=NO-1+IT`)

#### Class view

```c++
class DTLZ6 final : public DTLZ
```