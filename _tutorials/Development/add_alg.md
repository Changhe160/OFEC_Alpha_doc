---
title: Add Algorithm
category: Development
order: 4
---

>All algorithm objects in the platform are classes inherited from the base class [`algorithm`](../../Core/algorithm/algorithm).

- a
{:toc}

### Definition

An algorithm object should:
1. own at least one [`solution`](../../Core/algorithm/solution) as the candidate solution;
1. define how to initialize its added data members in [`initialize()`](../../Core/algorithm/algorithm#member-function);
1. define how to optimize the candidate solution in [`run_()`](../../Core/algorithm/algorithm#member-function);
1. define what to record for measurement in [`record()`](../../Core/algorithm/algorithm#member-function).

Beside, [`terminating()`](../../Core/algorithm/algorithm#member-function) is designed to be used in [`run_()`](../../Core/algorithm/algorithm#member-function) for temination checking, and it has a default implementation in [`algorithm`](../../Core/algorithm/algorithm).

>The default termination condition is [`termination`](../../Core/algorithm/termination), under which the algorithm terminates when the maximum number of evaluations is reached. 

Here is an simple example:
```c++
class heuristic : public algorithm {
protected:
    solution<> m_s;         // Candidate solution
public:
    heuristic(param_map& v);
    void initialize();      // Initialze m_s
    void run_() {
        while (!terminating())
            iterate();
    }
    void record();
protected:
    void iterate();         // Local search around m_s
}:
```
> [`solution`](../../Core/algorithm/solution) is a class template, whose decision variable encoding and objective type are template parameters. The default parameters are set to real numbers.

For population-based algorithms, it is recommended to use [`population`](../../Core/algorithm/population) instead of `vector<solution>`.

```c++
class evolutionary_algorithm : public algorithm {
protected:
    population<individual<>> m_pop; // Candidate population
public:
    evolutionary_algorithm(param_map& v);
    void initialize() {
    	m_pop.initialize();         // Initialize m_pop
    	m_pop.evaluate();           // Evaluate m_pop
    }
    void run_() {
        while (!terminating())
            m_pop.evolve();         // Evolve m_pop
    }
    void record();
}:
```

>[`population`](../../Core/algorithm/population) is also a class template to support different kinds of individual types. The individual type must be class derived from [`individual`](../../Core/algorithm/individual), which is inherited from [`solution`](../../Core/algorithm/solution).

### Output measurement

Modify the content of `headers` in `before_run()` at "*/run/user_initialization.cpp*":
```c++
void before_run() {
    std::vector<std::string> headers = {"Evaluations", "Best Objective"};
    measure::initialize(global::ms_arg.at("numRun"), headers);
}
```
Call `output_progr()` and `output_final()` in `after_run()`:
```c++
void after_run() {
    measure::get_measure()->output_progr();
    measure::get_measure()->output_final();
}
```
In member function `record()` call `record(...)`;

```c++
void algorithm::record() {
    size_t evals = global::ms_global->m_problem->evaluations();
    real best = problem::get_sofar_best<solution<>>(0)->objective(0);
    measure::get_measure()->record(global::ms_global.get(), evals, best);
}
```

### Registration

1. In the file "*/run/include_algorithm.h*" include the header file:
```c++
#include "../instance/algorithm/heuristic.h"
#include "../instance/algorithm/evolutionary_algorithm.h"
```
1. In the file "*/run/user_initialization.cpp*" use the `REGISTER()` macro to register:
```c++
REGISTER(algorithm, heuristic, "heuristic", std::set<problem_tag>({ problem_tag::GOP, problem_tag::ConOP }));
REGISTER(algorithm, evolutionary_algorithm, "EA", std::set<problem_tag>({ problem_tag::GOP, problem_tag::ConOP }));
```
> An algorithm is allowed to run on a problem only when the algorithm have all the problem tags the problem have. 