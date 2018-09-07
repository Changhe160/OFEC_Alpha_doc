---
title: problem
last_updated: Aug 13, 2018 by J. Wang
sidebar: API_sidebar
permalink: Problem_problem.html
folder: Problem
---
`class problem`

## Data members

|Name                      |Information                                      			 |
|--------------------------|-------------------------------------------------------------|
|***m_name***              |The name of problem											 |
|***m_variable_size***     |The number of variables										 |
|***m_objective_size***    |The number of objectives								     |
|***m_opt_mode***          |The [optimization mode][Other_enums] of each objective       |
|***m_tag***               |[Problem tags][Other_enums] of the problem					 |
|***m_parameters***        |The [parameter map][Other_enums] of the problem				 |
|***m_effective_eval***    |The number of evaluations used by algorithm					 |
|***m_total_eval***        |The total number of evaluations								 |
|***m_eval_monitor***      |Whether call **update_objective_minmax**() at each evaluation|
|***m_objective_accuracy***|The precision of objective									 |
|***m_solved***            |Whether all given optima have been found					 |
|***m_constraint_type***   |The [constraint type][Other_enums] of each constraint        |

## Member functions

**Note:** &nbsp;
&#9744; empty, to be override &nbsp;
&#9745; filled, but overridable &nbsp;
&#8718; filled and final 

|Name                                                     |Function                                                                                                                         |
|---------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
|&#8718; **(constructor)**(*name*, *size_var*, *size_obj*)|Initialization of ***m_name***, ***m_variable_size***, ***m_objective_size***, ***m_opt_mode*** and ***m_tag***		            |
|&#9745; **copy**(*pro*)                                  |Copy *pro* to the problem																							            |
|&#8718; **name**()                                       |Return ***m_name***																								                |
|&#8718; **variable_size**()                              |Return ***m_variable_size***																							            |
|&#9745; **resize_variable**(*n*)                         |Resize ***m_variable_size***																							            |
|&#8718; **objective_size**()                             |Return ***m_objective_size***																						            |
|&#9745; **resize_objective**(*n*)                        |Resize ***m_objective_size*** and ***m_opt_mode***																                |
|&#8718; **opt_mode**()                                   |Return ***m_opt_mode***																								            |
|&#8718; **opt_mode**(*i*)                                |Return the optimization mode of the *i*-th objective																	            |
|&#8718; **set_opt_mode**(*mode*, *i*)                    |Set the optimization mode of the *i*-th objective to *mode*															            |
|&#8718; **has_tag**(*tag*)                               |Check whether *tag* is included in ***m_tag***												        				            |
|&#8718; **set_tag**(*tags*)                              |Set ***m_tag*** to *tags*																							            |
|&#8718; **add_tag**(*tags*)                              |Add *tags* into ***m_tag***																							            |
|&#8718; **parameters**()                                 |Return ***m_parameters***																							            |
|&#9745; **update_parameters**()                          |Update the informations of ***m_name***, ***m_variable_size***, ***m_opt_mode*** and ***m_effective_eval*** in ***m_parameters***|
|&#8718; **evaluate**(*sol*, *call*, *effec*)             |Call **evaluate_**(*sol*, *call*, *effec*, true); Call **update_objective_minmax**() if ***m_eval_monitor*** is true	            |
|&#8718; **evaluations**()                                |Return ***m_effective_eval***																						            |
|&#8718; **total_evaluations**()                          |Return ***m_total_eval***																							            |
|&#8718; **set_eval_monitor_flag**(*flag*)                |Set ***m_eval_monitor*** to *flag*																					            |
|&#8718; **solved**()                                     |Return ***m_solved***																								            |
|&#8718; **num_constraints**()                            |Return the number of constraints 																					            |
|&#8718; **is_equality_constraint**(*i*)                  |Check whether the *i*-th constraint is a equality constraint															            |
|&#9744; **initialize**()                                 |Initialization of the problem																						            |
|&#9744; **evaluate_**(*sol*, *call*, *effec*, *const*)   |Evaluation process of the problem																					            |
|&#9744; **initialize_solution**(*sol*)                   |Initialize the variables of solution *sol*																			            |
|&#9744; **same**(*sol1*, *sol2*)                         |Check whether *sol1* and *sol2* are equal solutions																	            |
|&#9744; **variable_distance**(*sol1*, *sol2*)            |Calculate the distance between variables of two solutions *sol1* and *sol2*											            |
|&#9744; **variable_distance**(*var1*, *var2*)            |Calculate the distance between two variables *var1* and *var2*														            |
|&#9744; **check_boundary_violation**(*sol*)              |Check whether any one of *sol*'s variables violates boundary															            |
|&#9744; **check_constraint_violation**(*sol*)            |Check whether any one of *sol*'s variables violates constraint														            |
|&#9744; **feasible_ratio**()                             |Return the ratio of feasible area to total area in the decision space												            |
|&#9744; **is_optimal_given**()                           |Return whether optimal solutions of the problem are given														                |

## Static data members

|Name                     |Information                                      	|
|-------------------------|-----------------------------------------------------|
|***ms_minmax_objective***|The best and worst so far solutions of each objective|

## Static member functions

|Name                                            |Function                                     |
|------------------------------------------------|---------------------------------------------|
|**get_sofar_best**\<**Solution**\>(*i*) |Return the best solution of the *i*-th objective     |
|**get_sofar_worst**\<**Solution**\>(*i*)|Return the worst solution of the *i*-th objective    |
|**update_objective_minmax**()                   |Update ***ms_minmax_objective***             |


{% include links.html %}