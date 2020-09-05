---
title: Installation
category: Tutorial
order: 1
---

>OFEC does not rely on libraries other than **C++ STL 14**. So to intall OFEC, just download or git clone it from its [**GitHub repo**](https://github.com/Changhe160/OFEC_Alpha), and compile it by the following recommended ways:

#### Windows (Visual Studio)

1. Install **Visual Studio**;
1. Open the VS project file *OFEC.sln* or *OFEC.vcxproj*;
1. Set the *Windows SDK Version* and the *Platform Toolset* (find them in *Project->Properties->General*) correctly;
1. Set the *Object File Name* (find it in *Project->Properties->C/C++->Output Files*) to `$(IntDir)/%(RelativeDir)/` (**NECESSARY**, there exist source files with the same name);
1. Build the solution.

#### Linux (terminal)

1. Open the terminal in the root directory of OFEC;
1. Run `gcc -v` and `make -v` to make sure **gcc** and **make** have been installed. If not run `sudo apt install gcc make`;
1. Run `make` to compile (OPTIONAL: run `make -j8 |& grep error` to compile it in parallel and grep the error informations ).


#### MacOS (CLion)

1. Install **CLion**;
1. Open the root directory of OFEC in **CLion** ;
1. Make sure the CMake project has been reloaded successfully;
1. Build the project.