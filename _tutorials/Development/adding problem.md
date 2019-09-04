---
title: Adding problem
category: Development
order: 3
---
- a
{:toc}

>All problem objects in OFEC are classes inherited from the base class [`problem`](../../Core/problem/problem).

A problem object must:
1. define how to **calculate** the **objective values** and the **constraint violation** of a given solution `s` in the member function `evaluate_(s)`;
1. define how to **initialize** the **decision variables** of a given solution `s` in the member function `initialize_solution(s)`;
1. define how to **calculate** the **distance in decision space** between two given solutions `s1` and `s2` in the member function `variable_distance(s1, s2)`.

Besides:
- the constructor function `problem(v)` recieve a parameter of type `param_map&` to obtain informations from command arguments;
- the member function `initialize()` is used to initialize the data members if necessary;

---

#### Declaration

[One Max](../../Instance/problem/one max) is a simple example for combinatorial optimization algorithms.

```c++
class one_max : public problem {
protected:
    optima<variable_vector<int>, real> m_optima;
public:
    void initialize() override ;// Initialize the m_optima
    evaluation_tag evaluate_(solution_base&, caller, bool, bool) override;
    void initialize_solution(solution_base&) const override;
    real variable_distance(const solution_base&, const solution_base&) const override;
}
```

For continuous optimization problem, it is highly recommended to make it inherited from [`continuous`](../../Core/problem/continuous).

```c++
class sphere : public continuous {
public:
    void initialize()   // Initialize the m_domain and m_optima
    //evaluation_tag evaluate_(solution_base&, caller, bool, bool);
    void evaluate_objective(real*, vector<real>&);
    //void initialize_solution(solution_base&) const;
    //real variable_distance(const solution_base&, const solution_base&) const;
}
```
- `m_domain` and `m_optima` are added in [`continuous`](../../Core/problem/continuous);
- The member function `initialize_solution(s)` has been overridden in [`continuous`](../../Core/problem/continuous) as a **uniform random initialization** method;
- The member function `evaluate_(s)` has been overridden in [`continuous`](../../Core/problem/continuous) as a mixture of `evaluate_objective(x, obj)` and `evaluate_obj_nd_con(x, obj, con)`;
- The member function `variable_distance(s1, s2)` has been overridden in [`continuous`](../../Core/problem/continuous) as a euclidean distance calculation method.

---

#### Registration

1. In the file "/run/include_problem.h" include the header file that declares the class.
2. In the file "/run/user_initialization.cpp" use the `REGISTER()` macro to register the class, where:
	- the 3rd parameter is the **string command** of your defined problem;
	- the 4th parameter is the [**problem tag**](../../Core/definition/#problem-tags) of problem;