---
title: Running
last_updated: Sep 7, 2018 by J. Wang
sidebar: guide_sidebar
permalink: Tutorial_running.html
folder: Tutorial
---

## Run OFEC on Windows

### Run OFEC in **Visual Studio**

In **Project**->**Properties**->**Debugging** input command arguments and then **Debug**->**Start Debugging**.

### Run OFEC in **cmd** console

Copy the executable file "OFEC.exe" from the directory "/x64/release/" or "/x86/release/" to the root directory "/".

Enter into the **root directory of this project** in the **cmd** console and run this command:
```
OFEC [command arguments]
```

## Run OFEC on Linux
In the root directory run this command:
```
bin/r [command agruments]
```

## Examples of Command Arguments
**Global Optimization Problem**

`PN=Sphere ND=2 AN=CRDE PS=100 ME=10000 SF=100`

`PN=Sphere ND=2 AN=CRDE PS=100 ME=10000 SF=100`

**Multi-Modal Optimization Problem**

`PN=Sphere ND=2 AN=CRDE PS=100 ME=10000 SF=100`

`PN=Sphere ND=2 AN=CRDE PS=100 ME=10000 SF=100`

**Constrainded Optimization Problem**

`PN=Sphere ND=2 AN=CRDE PS=100 ME=10000 SF=100`

`PN=Sphere ND=2 AN=CRDE PS=100 ME=10000 SF=100`

**Multi-Objective Optimization Problem**

`PN=Sphere ND=2 AN=CRDE PS=100 ME=10000 SF=100`

`PN=Sphere ND=2 AN=CRDE PS=100 ME=10000 SF=100`

## Output experimental results

Different algorithms may output different data, so several steps need following to output experimental result:
1. In ["/run/user_initialization.cpp"](https://github.com/Changhe160/OFEC_Alpha/blob/master/run/user_initialization.cpp) find function `void before_run()`.
In `void before_run()`, call function `measure::initialize(...)`. 
The first parameter must be `global::ms_arg.at("numRun")`.
The second parameter are a vector of string which denotes the headers of recorded information. For example:
```cpp
void before_run() {
	measure::initialize(global::ms_arg.at("numRun"), std::vector<std::string>({ "Evaluations", "Best objective value" }));
}
```
2. In the source file of the algorithm to run, create a member function `void record()` (if there already exists one then modify it).
In `void record()` call function `measure::get_measure()->record(...)`.
The first parameter must be `global::ms_global.get()`.
The **rest parameters are the information you want to record**. For example:
```cpp
void CRDE::record()	{
	size_t evals = CONTINOUS_CAST->evaluations();
	real best = problem::get_sofar_best<solution<>>(0)->objective(0);
	measure::get_measure()->record(global::ms_global.get(), evals, best);
}
```
The information will be recorded **every certain evaluations**.
The **sample frequency** is determined by the value of `SF` in the command arguments.
**Note that**, since we called `problem::get_sofar_best()` here, we must **turn on the evaluation monitor switch** 
by calling `global::ms_global->m_problem->set_eval_monitor_flag(true)` before running the algorithm.
3. In ["/run/user_initialization.cpp"](https://github.com/Changhe160/OFEC_Alpha/blob/master/run/user_initialization.cpp) find function `void after_run()`.
In `void after_run()`, call function `measure::get_measure()->output_progr()` to output the information every certain evaluations, 
and call funtion `measure::get_measure()->output_final()` to output the last recorded information. For example:
```cpp
void after_run() {
	measure::get_measure()->output_progr();
	measure::get_measure()->output_final();
}
```
4. **RECOMPILE** the project;
5. Make sure the command arguments are correct. Aftering running, the results will be generated in the directory "/result/".

## Add user-defined algorithm or problem.

See [Development][Tutorial_development] to know how to add your own algorithms or benchmark problems into this platform.

{% include links.html %}