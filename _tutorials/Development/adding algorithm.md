---
title: Adding algorithm
category: Development
order: 3
---
- a
{:toc}

>All algorithm objects in the platform are classes inherited from the base class [`algorithm`](../../Core/algorithm/algorithm).

An algorithm object must:
1. own at least one [`solution`](../../Core/algorithm/solution) as the candidate solution;
1. define how to initialize the candidate solution in the member function `initialize()`;
1. define how to optimize the candidate solution in the member function `run_()`;
1. define what to record for experimental results in the member function `record()`.

Besides:
- the constructor function `algorithm(v)` recieve a parameter of type `param_map&` to obtain informations from command arguments;
- the member function `terminating()` is designed to be used in `run_()` to terminate the algorithm when the criterion is fulfilled

>The default termination condition is [`termination`](../../Core/algorithm/termination), under which the algorithm terminates when the maximum number of evaluations is reached. 
 
---

#### Declaration

[Simulated Annealing](../../Instance/algorithm/simulated annealing) is a simple example for single solution algorithms.

```c++
class simulated_annealing : public algorithm {
protected:
    solution<> m_s; // Candidate solution
public:
    simulated_annealing(param_map& v);
    void initialize();
    void run_() {
        while (!terminating())
            iterate();
    }
    void record();
    //bool terminating(); Use the default criterion
protected:
    void iterate();
}:
```

For population-based algorithms, it is highly recommended to define a data member `m_pop` of type [`population`](../../Core/algorithm/population).

```c++
class evolutionary_algorithm : public algorithm {
protected:
    population<individual<>> m_pop; // Candidate population
public:
    evolutionary_algorithm(param_map& v);
    void initialize() {
    	m_pop.initialize();  // Initialize population
    	m_pop.evaluate();    // Evluate population
    }
    void run_() {
        while (!terminating())
            m_pop.evolve();
    }
    void record();
    //bool terminating(); Use the default criterion
}:
```

>**Note that**, [population](Core/algorithm/population) is a class template. 
The template parameter determines the type of [`individual`](Core/algorithm/individual), which is inherited from [`solution`](Core/algorithm/solution),
and serves as the basic unit of the population.

Furthermore, if the algorithm is a variant of the canonical DE or PSO, it is recommended to make the type of `m_pop` inherited from [`DE::population`](../../Instance/algorithm/canonical DE/#depopulation) or [`swarm`](../../Instance/algorithm/standard PSO/#swarm).

---

#### Output informations

- In function `before_run()` (in "/run/user_initialization.cpp") modify the content of `headers`.

```c++
void before_run() {
    std::vector<std::string> headers = {"Evaluations", "Best Objective"};
    measure::initialize(global::ms_arg.at("numRun"), headers);
}
```

- In member function `record()` call `measure::get_measure()->record(args ...)`;

```c++
void algorithm::record() {
    size_t evals = global::ms_global->m_problem->evaluations();
    real best = problem::get_sofar_best<solution<>>(0)->objective(0);
    measure::get_measure()->record(global::ms_global.get(), evals, best);
}
```

---

#### Registration

1. In the file "/run/include_algorithm.h" include the header file declaring the class.
2. In the file "/run/user_initialization.cpp" use the `REGISTER()` macro to register the class.
	- The third parameter is the **identification** of your defined algorithm or problem in command arguments.
	- The fourth parameter is the [problem tag](../../Core/definition/#problem-tags) of the algorithm or problem.

> An algorithm is allowed to run on a problem only when it have all the problem tags the problem have. 