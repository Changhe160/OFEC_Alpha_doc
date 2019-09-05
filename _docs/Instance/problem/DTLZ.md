---
title: DTLZ
category: Instance
subcategory: problem
order: 22
---

#### Reference

Deb, K., Thiele, L., Laumanns, M., & Zitzler, E. (2005).
"Scalable test problems for evolutionary multiobjective optimization".
In*Evolutionary multiobjective optimization* (pp. 105-145). Springer London.

#### Class view
```c++
class DTLZ : public continuous
```
Link: [`continuous`](../../../Core/problem/continuous)

#### Member functions

|Name|Utility|
|-|-|
|`initialize()`||
|`LoadPF()`||
|`generate_PF()`||

### DTLZ1

#### Command line arguments example

`PN=MOP_DTLZ1 IT1=5 NO=3` (`ND=NO-1+IT1`)

#### Class view

```c++
class DTLZ1 final : public DTLZ
```

### DTLZ2

#### Command line arguments example

`PN=MOP_DTLZ2 IT1=10 NO=3` (`ND=NO-1+IT1`)

#### Class view

```c++
class DTLZ2 final : public DTLZ
```

### DTLZ3

#### Command line arguments example

`PN=MOP_DTLZ3 IT1=10 NO=3` (`ND=NO-1+IT1`)

#### Class view

```c++
class DTLZ3 final : public DTLZ
```

### DTLZ4

#### Command line arguments example

`PN=MOP_DTLZ4 IT1=5 NO=3` (`ND=NO-1+IT1`)

#### Class view

```c++
class DTLZ4 final : public DTLZ
```

### DTLZ6

#### Command line arguments example

`PN=MOP_DTLZ6 IT1=20 NO=3` (`ND=NO-1+IT1`)

#### Class view

```c++
class DTLZ6 final : public DTLZ
```
