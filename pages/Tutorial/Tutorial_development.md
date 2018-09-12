---
title: Development
last_updated: Sep 12, 2018 by J. Wang
sidebar: guide_sidebar
permalink: Tutorial_development.html
folder: Tutorial
---

This page briefly shows how to add **user-defined algorithms** or **benchmark problems** into this platform. To get more detailed information please refer to [the OFEC API][Other_global].

## Solution

---------------------------------------------

In this plotform, [`solution`][Algorithm_solution] is defined as class template, whose first template parameter `VariableEncoding` determines the representaion of the solution's decision variables,
and its second template parameter `ObjetiveType` determines the type of the solution's objective values.

---------------------------------------------

## Problem

---------------------------------------------

An **user-defined problem** must be a **derived class** inherited from class [problem][Problem_problem].
In our standard, you must at least
* define a `(constructor)` function that takes one `param_map&` parameter, which is used to **determine the properties given in the command arguments**;
* override the member function `initialize`, which is used to **determine the properties not given in the command arguments**;
* override the member function `initialize_solution`, which is used to **initialize a solution's decision variables**;
* override the member function `evaluate_`, which is used to **calculate a solution's objective values**.

---------------------------------------------

If the user-defined problem is a **continuous optimization** problem, it is highly recommended to make it inherited from class [continuous][Problem_continuous].
You still need to
* define the `(constructor)` function that takes one `param_map&` parameter, and override the member function `initialize`.

The member function `initialize_solution` has been overridden as a **uniform random initialization** method.

The member function `evaluate_` has been overridden to add a **calculation for a solution's constraint violation value**.

If there is no constraint on the problem, then you only need to
* override the member function `evaluate_objective`, which is used to  **calculate a solution's objective values**.

---------------------------------------------

## Algorithm

---------------------------------------------

An **user-defined algorithm** must be a **derived class** inherited from class [algorithm][Algorithm_algorithm]. 
Firstly, you must
* define a `(constructor)` function that takes one `param_map&` parameter, which is used to **determine the properties given in the command arguments**;
* override the member function `initialize`, which is used to **determine the properties not given in the command arguments**, and to **complete initialization of the algorithm**;
* override the member function `run_`, which is the **whole running process after initialization**;

The member function `terminating` defines a default termination condition, 
under which the algorithm terminates when the maximum number of evaluations (as determined by `ME` in command arguments) is reached.
So if you do not want to use this you also need to
* override the member function `terminating` to define the termination condition.

---------------------------------------------

If the algorithm is **based on population**, it is highly recommended to create a derived class inherited from class [population][Algorithm_population].
You still need to
* define the `(constructor)` function that takes one `param_map&` parameter.

The member function `initialize` has been overridden to **initialize and evaluate the population**.
The member function `run_` has been overridden to **repeatly evolve the population** until the terminatin condition is reached.
But the evolving process is not given. So you need to 
* override the member function `evolve`, which defines the **operation in a single iteration**.

---------------------------------------------

Furthermore, if the algorithm is a variant of the canonical DE or PSO, it is recommended to create a derived class inherited from class [DE::population][Algorithm_DE_pop] or class [PSO::population][Algorithm_PSO_pop].

---------------------------------------------

## Registration

Before use the user-defined algorithm or problem classes, you must register them:
1. In the file ["/run/include_algorithm.h"](https://github.com/Changhe160/OFEC_Alpha/blob/master/run/include_algorithm.h) 
or ["/run/include_problem.h"](https://github.com/Changhe160/OFEC_Alpha/blob/master/run/include_problem.h) include the header file of the class.
2. In the file ["/run/user_initialization.cpp"](https://github.com/Changhe160/OFEC_Alpha/blob/master/run/user_initialization.cpp) use the `REGISTER()` macro to register the class.
The third parameter is the **identification** of your defined algorithm or problem in [Command Arguments](Tutorial_running.html#examples-of-command-arguments).
The fourth parameter is the [problem tag](Other_enums.html#problem_tag) of the algorithm or problem.
To run an algorithm on a problem, they must have **at least one common tag**. 

Then you can use your defined algorithm or problem by following the [running][Tutorial_running] process.

{% include links.html %}