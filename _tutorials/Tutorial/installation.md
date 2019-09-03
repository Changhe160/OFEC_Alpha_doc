---
title: Installation
category: Tutorial
order: 1
---

Git the repository or download the zip file from [OFEC Alpha](https://github.com/Changhe160/OFEC_Alpha).

#### Compile OFEC in Windows
For Windows PC, it is recommended to use **Visual Studio 2017/2019** to compile OFEC. Open the project file **OFEC.sln**. Then Use **Build**->**Build Solution** to complile the project.

>
1. Make sure **Windows SDK Version** and **Platform Toolset** (you can find them in **Project**->**Properties**->**General**) is OK.
1. Set the solution configuration to **Release** to run experiments faster.

#### Compile OFEC in Linux Shell

Make sure `g++` and `make` have been installed in your Linux. If not run
```
sudo apt install g++ make
```
Then `cd` into the ***root directory*** of the project and run `make`. You can also add some optional commands to ***compile in parallel*** and ***grep the error informations***:
```
make -j8 |& grep error
```
