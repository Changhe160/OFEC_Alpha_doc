---
title: Running
category: Tutorial
order: 2
---

Algorithm, problem, and some other experimental parameters are set by command line arguments. The form of command line arguments is like: 
`ME=20000 SF=100 NR=4 PN=GOP_CLASSICAL_sphere ND=2 AN=DE-rand-1 PS=100`.

> Refer to the [list of command line arguments](../cmd_line_args)  to understand their meaning. For problem and algorithm examples, refer to their APIs to see the required arguments.

To run OFEC from the terminal, append the command line arguments to the application
-  *console/bin/r* compiled by **gcc** and **make**;
-  *console/x64/Debug/OFEC.exe* built by **Visual Studio**;
-  *console/cmake-build-debug/OFEC* built by **CLion**.

To run OFEC in IDEs, enter the command line arguments in 
- *Project->Properties->Debugging->Command Arguments* in **Visual Studio**;
- *Run->Edit Configurations->Program arguments* in **CLion**.

Aftering running, the results will be generated in the "/result/" directory (you need to create this directory yourself). 