---
title: Installation
last_updated: Aug 13, 2018 by J. Wang
sidebar: guide_sidebar
permalink: Tutorial_installation.html
folder: Tutorial
---

## Download OFEC
You can Git the repository or download the zip file from [OFEC Aplha](https://github.com/Changhe160/OFEC_Alpha). We recommend using the former to make it more convenient for you to get updates and feedback questions.

## Compile OFEC on Windows
It is recommended to use **Visual Studio 2017** to compile OFEC on Windows. Open the project file **OFEC.sln** in the root directory, and then in **Project**->**Properties**->**General** change the **Windows SDK Version** and **Platform Toolset** to your installed versions.

In order to run experiments faster, change the solution configuration to **Release**. Then Use **Build**->**Build Solution** to complile the project.

## Compile OFEC on Linux
We have writen the makefile, so make sure **g++** and **make** have been installed on your Linux, and then in the root directory run this command:
```
make
``` 
You can also add some optional commands to compile in parallel and grep the error informations:
```
make -j8 |& grep error
```
To run OFEC, see [Running][Tutorial_running].

{% include links.html %}