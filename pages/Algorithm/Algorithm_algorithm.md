---
title: algorithm
last_updated: Aug 13, 2018 by J. Wang
sidebar: API_sidebar
permalink: Algorithm_algorithm.html
folder: Algorithm
---
`class algorithm`
## Data members

|Name            |Type                                               |Information                   |
|----------------|---------------------------------------------------|------------------------------|
|**m_name**      |std::string                                        |Algorithm's name              |
|**m_term**      |std::unique_ptr\<[termination][Other_termination]\>|Algorithm's terminal condition|
|**m_parameters**|[param_map][Other_aliases]                       |Algorithm's parameters        |

## Member functions

**Note:** &nbsp;
&#9744; empty, to be override &nbsp;
&#9745; filled, but overridable &nbsp;
&#8718; filled and final 

|Name                              |Function                                                                |
|----------------------------------|------------------------------------------------------------------------|
|&#9744; **initialize**()          |Intialization of the algorithm                                          |
|&#9744; **run_**()                |Running process of the algorithm                                        |
|&#9744; **record**()              |Record operation to do each sample frequency                            |
|&#8718; **(constructor)**()       |Default constructor                                                     |
|&#8718; **(constructor)**(*name*) |Initialization of **m_name**                                            |
|&#8718; **(constructor)**(*alg*)  |Copy/Move from *alg*                                                    |
|&#8718; **operator=**(*alg*)      |Copy/Move from *alg*                                                    |
|&#8718; **set_name**(*name*)      |Set **m_name** to *name*                                                |
|&#8718; **name**()                |Return **m_name**                                                       |
|&#8718; **set_termination**(*ter*)|Set **m_term** to *ter*                                                 |
|&#8718; **terminating**()         |Check whether the algorithm reaches terminal condition                  |
|&#8718; **terminated**()          |Return whether the algorithm has terminated                             |
|&#8718; **duration**()            |Return the running time of the algorithm                                |
|&#8718; **update_parameters**()   |Update the informations of **m_name** and **m_term** in **m_parameters**|
|&#8718; **parameters**()          |Return **m_parameters**                                                 |
|&#8718; **run**()                 |Start the running process and update states after termination           |

{% include links.html %}