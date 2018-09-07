---
title: Development
last_updated: Sep 7, 2018 by J. Wang
sidebar: guide_sidebar
permalink: Tutorial_development.html
folder: Tutorial
---

This page briefly shows how to add **user-defined algorithms** or **benchmark problems** into this platform. To get more detailed information please refer to [the OFEC API][Other_global].

## Problem

---------------------------------------------

An **user-defined problem** must be a **derived class** inherited from class [problem][Problem_problem].
In our standard, you must
* define the `(constructor)()` function to **allocate memory** for data members,
* override the member function `initialize()` to **initialize parameters** of the problem.

In addtion, two virtual member functions of class problem--i.e., `initialize_solution()` and `evaluate_()`, must be override:
* `initialize_solution()` defines how to **initialize** a solution's **decision variables**.
* `evaluate_()` defines how to **evaluate** a solution's **objective values** according to its decision variables.

---------------------------------------------

If the user-defined problem is a **continuous optimization** problem, it is highly recommended to make it inherited from class [continuous][Problem_continuous].
You still need to
* define the `(constructor)()` function and override `initialize()`.

But member function `initialize_solution()` has already been override in class continuous in a default **uniform random** manner,
and `evaluate_()` has been override to add the **calculation of constraint violation**.
If your problem has no addtional constraint condition, only one virtual member function of class continous--i.e., `evalute_objective()`, must be override.
* `evaluate_objective()` defines how to **evaluate** a solution's **objective values** according to its decision variables.

---------------------------------------------

## Algorithm

---------------------------------------------

An **user-defined algorithm** must be a **derived class** inherited from class [algorithm][Algorithm_algorithm]. 
Similar to the problem classes, you must
* define the `(constructor)()` function to **allocate memory** for data members,
* override the member function `initialize()` to **initialize parameters** of the algorithm.

In addtion, one virtual
* member function `run_` must be override to define **how the algorithm runs**.

---------------------------------------------

If the algorithm is **based on population**, it is highly recommended to create a derived class inherited from class [population][Algorithm_population].
You still need to
* define the `(constructor)()` function and override `initialize()`.

But member function `run_` has already been override to **repeatly evolve the population**, and only one virtual
* member function `evolve_` must be override to define the **operation in a single iteration**.

---------------------------------------------

Furthermore, if the algorithm is a variant of the canonical DE or PSO, it is recommended to create a derived class inherited from class [DE::population][Algorithm_DE_pop] or class [PSO::population][Algorithm_PSO_pop].

---------------------------------------------

## Registration

Before use the user-defined algorithm or problem classes, you must register them:
1. In the file ["/run/include_algorithm.h"](https://github.com/Changhe160/OFEC_Alpha/blob/master/run/include_algorithm.h) 
or ["/run/include_problem.h"](https://github.com/Changhe160/OFEC_Alpha/blob/master/run/include_problem.h) include the header file of the class.
2. In the file ["/run/user_initialization.cpp"](https://github.com/Changhe160/OFEC_Alpha/blob/master/run/user_initialization.cpp) use the `REGISTER()` macro to register the class.
The third parameter is the **identification** of your defined algorithm or problem in [Command Arguments](Tutorial_running.html#examples-of-command-arguments).
The fourth parameter is the [problem tag](Other_enums.html#problem_tag) of your defined algorithm or problem.
In the running process, the algorithm and the problem must have **at least one common tag**. 

Then you can use your defined algorithm or problem by following the [running][Tutorial_running] process.

{% include links.html %}