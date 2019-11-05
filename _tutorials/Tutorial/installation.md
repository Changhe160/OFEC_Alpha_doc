---
title: Installation
category: Tutorial
order: 1
---

>OFEC does not rely on libraries other than **C++ STL 14**. So to intall OFEC, just download or git clone it from its [**GitHub repo**](https://github.com/Changhe160/OFEC_Alpha), and compile it by the following recommended ways:

#### Windows

1. Install **Visual Studio**;
1. Open the VS project file *OFEC.sln* or *OFEC.vcxproj*;
1. Set the *Windows SDK Version* and the *Platform Toolset* (find them in *Project->Properties->General*) correctly;
1. Set the *Object File Name* (find it in *Project->Properties->C/C++->Output Files*) to `$(IntDir)/%(RelativeDir)/` (**NECESSARY**, we have source files with same name);
1. Build the solution.

#### Linux

1. Open the terminal in the root directory of OFEC;
1. Run `gcc -v` and `make -v` to make sure **gcc** and **make** have been installed. If not run `sudo apt install gcc make`;
1. Run `make` to compile. You can also add some optional commands to compile it in parallel and grep the error informations `make -j8 |& grep error`.


#### MacOS

1. Install **gcc** by running `brew install gcc` in the terminal; 
1. Install **Clion**;
1. Open the root directory of OFEC in **Clion** ;
1. Make sure the CMake project is reloaded successfully;
1. Go to *Preference->Build, Excecution, Deployment->Toolchains*;
1. Change the *C++ compiler* to **g++**  (e.g., "/usr/local/bin/g++-9");
1. Build the project.