---
title: Adding problem
category: Development
order: 3
---

>The type of problem instance should be class derived from the base class [`problem`](../../Core/problem/problem).

- a
{:toc}

### Definition

A problem object must:
1. define how to initialize the added data members (e.g., optimal solutions and search domain) in [`initialize()`](../../Core/problem/problem#member-function);
1. define a default initialization method for **decision variables** of a given solution in [`initialize_solution(s)`](../../Core/problem/problem#member-function);
1. define how to calculate the **objective values** and the **constraint violation** of a given solution in [`evaluate_(s)`](../../Core/problem/problem#member-function);
1. define the distance between two decision variables or two solutions in [`variable_distance(x1, x2)`](../../Core/problem/problem#member-function) or [`variable_distance(s1, s2)`](../../Core/problem/problem#member-function);
1. define how to check whether two solutions are the same in [`same(s1, s2)`](../../Core/problem/problem#member-function).


For a combinatorial optimization algorithm, just make it inherited from [`problem`](../../Core/problem/problem):
```c++
class one_max : public problem {
protected:
    optima<variable_vector<int>, real> m_optima;
public:
    void initialize() override ;   // Initialize m_optima
    void initialize_solution(solution_base&) const override;
    evaluation_tag evaluate_(solution_base&, caller, bool, bool) override;
    real variable_distance(const solution_base&, const solution_base&) const override;
    real variable_distance(const variable_base&, const variable_base&) const override;
    bool same(const solution_base&, const solution_base&) const override;
```

For a continuous optimization problem, it is recommended to make it inherited from [`continuous`](../../Core/problem/continuous) or [`function`](../../Core/problem/function) (which is derived from [`continuous`](../../Core/problem/continuous)).

```c++
class sphere : public function {
public:
    void initialize() override;   // Initialize m_domain m_optima
    void evaluate_objective(real*, vector<real>&) override;
}
```
- [`m_domain`](../../Core/problem/continuous#data-member) and [`m_optima`](../../Core/problem/continuous#data-member) are added in [`continuous`](../../Core/problem/continuous);
- [`initialize_solution(s)` `variable_distance(s1, s2)` `variable_distance(x1, x2)` `same(s1, s2)`](../../Core/problem/continuous#member-function) have been given in [`continuous`](../../Core/problem/continuous);
- [`evaluate_(s)`](../../Core/problem/continuous#member-function) has been given in [`continuous`](../../Core/problem/continuous) as a mixture of [`evaluate_objective(x, obj)`](../../Core/problem/continuous#member-function) and [`evaluate_obj_nd_con(x, obj, con)`](../../Core/problem/continuous#member-function);

### Registration

1. In the file "*/run/include_problem.h*" include the header file:
```c++
#include "../instance/problem/combination/one_max/one_max.h"
#include "../instance/problem/continuous/global/classical/sphere.h"
```
2. In the file "*/run/user_initialization.cpp*", use the `REGISTER(...)` macro to register:
```c++
REGISTER(problem, one_max, "ComOP_One_Max", std::set<problem_tag>({ problem_tag::ONEMAX, problem_tag::ComOP }));
REGISTER(problem, sphere, "GOP_CLASSICAL_sphere", std::set<problem_tag>({ problem_tag::GOP,problem_tag::ConOP }));
```
- the 3rd parameter is the name string to call the problem in command line arguments;
- the 4th parameter marks the [tags](../../Core/definition/#problem-tags) of the problem.