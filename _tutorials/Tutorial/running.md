---
title: Running
category: Tutorial
order: 2
---

To determine the algorithm, problem and some other experimental parameters, we need to pass necessary command line arguments to the application. The form of command line arguments is like: 
`ME=20000 SF=100 NR=4 PN=GOP_CLASSICAL_sphere ND=2 AN=DE-rand-1 PS=100`.

>Refer to [command line argument list](../command line argument list) to see their meanings.
For problem and algorithm instances, refer to their APIs to see the needed arguments.

To run OFEC:
- in **Visual Studio**, input the command line arguments in *Project->Properties->Debugging->Command Arguments*, and then start debugging;
- in **Clion**, input the command line arguments in *Run->Edit Configurations->Program arguments*and the start debugging. 

To run OFEC in terminal, just add the command line arguments to the application. If it is compiled:
- by **gcc** and **make**, the application is "console/bin/r";
- by **Visual Studio**, the application is "console/x64/Debug/OFEC.exe";
- by **Clion**, the application is "console/cmake-build-debug/OFEC";

Aftering running, the results will be generated in the directory "/result/" (you need to create this directory yourself). 