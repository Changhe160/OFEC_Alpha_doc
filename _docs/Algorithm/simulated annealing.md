---
title: Simulated annealing
category: Algorithm
order: 3
---

#### String command example

`AN=SA`

#### Reference

[S. Kirkpatrick, C. D. Gelatt Jr, and M. P. Vecchi. (1983).
"Optimization by Simulated Annealing".
*Science*. 220 (4598): 671–680.](https://doi.org/10.1126%2Fscience.220.4598.671)

#### Pseudocode

1. Let $s=s_0$
1. For $k\in \\{1, \ldots, k_{max}\\}$:
	1. T $\gets$ *temperature*($\frac{k_{max}}{k}$)
	1. Pick a random neighbour, $s_{new}\gets$ *neighbour*($s$)
	1. If *P*(*E*($s$), *E*($s_{new}$), T) $\leq$ *random*(0, 1)
		1. $s \gets s_{new}$
1. Output the final state $s$

#### Class view

```c++
class simulated_annealing : public algorithm
```
Link: [``algorithm``](../algorithm)

#### Added data members

|Name|Type|Utility|
|-|-|-|
|``m_k_max``|``size_t``|Maximum number of evalutions|
|``m_s``|[``solution<>``](../../Core/solution)|Candidate state (solution) $s$ |
|``m_s_new``|[``solution<>``](../../Core/solution)|Neighboring state $s_{new}$|

#### Overridden member functions

|Name|Utility|
|-|-|
|``initialize()``|Initialize and evalute $s$|
|``run_()``|Optimize $s$ according to Pseudocode 2.|
|``record()``|Record the number of evaluations and the error (difference of the first objective between the current best solution and the global optima)|

#### Added member functions

|Name|Utility|
|-|-|
|``temperature(val)``|The function *temperature* in Pseudocode 2.1.|
|``neighbour(s, s_new)``|The function *neighbour* in Pseudocode 2.2.|
|``P(s, s_new, T)``|The acceptance probability function *P* in Pseudocode 2.3.|