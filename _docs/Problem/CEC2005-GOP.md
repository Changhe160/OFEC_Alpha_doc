---
title: CEC2005-GOP
category: Problem
order: 10
---

#### Reference 

[Suganthan, P. N., Hansen, N., Liang, J. J., Deb, K., Chen, Y. P., Auger, A., & Tiwari, S. (2005).
"Problem definitions and evaluation criteria for the CEC 2005 special session on real-parameter optimization".
KanGAL report, 2005005, 2005.](http://www.cmap.polytechnique.fr/~nikolaus.hansen/Tech-Report-May-30-05.pdf)

### F01

#### Class view
```c++
namespace CEC2005 {
class F1_shifted_sphere : public sphere
}
```
Link: [`sphere`](../classical-GOP)

### Composition

#### Class view
```c++
namespace CEC2005 {
    class composition : public continuous
}
```
Link: [`continuous`](../continuous)

### F15

#### Properties

- Multi-modal
- Separable near the global optimum (Rastrigin)
- Scalable
- A huge number of local optima
- Different function’s properties are mixed together
- Sphere Functions give two flat areas for the function

#### Class view
```c++
namespace CEC2005 {
    class F15_hybrid_composition : public composition
}
```
Link: [`CEC2005::composition`](#composition)

### F25

#### Properties

- All settings are the same as F24 except no exact search range set for this test function: initialize population in [2,5]$^D$ , Global optimum is outside of the initialization range

#### Class view
```c++
namespace CEC2005 {
    class F25_rotated_hybrid_no_bound : public composition
}
```
Link: [`CEC2005::composition`](#composition)