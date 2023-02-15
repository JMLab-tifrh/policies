# Job submission policies and template scripts for HPCs
This is the documentation for job submission policies for the HPCs exclusive to the group members.

## List and details of resources



## general submission rules
<ol>
  <li> Always allocate the complete node for a single job submission. Since all simulations are always run on multiple seeds, multiple simulations, if needed, are to be run inside a single job script. An example has been provided later.</li>
  <li> Except, JMC, all other clusters have a maximum walltime (runtime) of 5 days (120 hrs). </li> 
  <li> It is advised to optimize the number of CPUs needed per simulation prior to longer runs. This ensures optimal usage of the computers. </li>
  <li> It is requested that users should output their trajectories in .xtc formats, unless explicitly needed, to reduce the storage space usage. Optionally, one should also output only the particles/atoms/groups which they would require. This would further reduce the storage space needed. </li>
  <li> Take regular backups and do not use the HPC's storage for storing data. The HPCs have limited storage space and its complete utilization is highly likely to cause a system crash. </li>
  <li> Each HPC has its own job submission limit which has been detailed in later sections. Please abide by those rules. In case of any special requirement, JM's authorization will be needed. The person should also let others know about this so as to avoid any unnecessary misunderstandings and clashes.
</ol>

## Details of maximum usage limit for each HPC:
| HPC name   | maximum submission limit per queue  |
|:----------:|-------------------------------------|
|JMC         | to be updated                       |
|ryzencluster|_ryzen9-3080_: 4 running + 1 queue = 5<br>_ryzen7-3080_: 1 running + 1 queue = 2<br>_ryzen9-2080_: 2 running + 1 queue = 3|
|ampere      |_ryzen_: 9 running + 2 queue = 11<br>epyc: 1/2 running + 1 queue=2/3|
|karplus     |_workq_: 8 running + 2 queue = 10|
<br><br>

## Using single node (scheduler less) computers
| computer name | usage type          | submission type  | policy                    |
|:-------------:|---------------------|------------------|---------------------------|
| maxwell2      | running simulations | manual submission| inform other before using.|
| pascal        | running simulations | manual submission| inform other before using.|
| north         | analysis only       | manual submission| use if CPUs are free. Please inform everyone<br>if you intend to use all the CPUs together.|
| turing        | ML, analysis        | manual submission| use if CPUs and GPU are free. Please inform everyone<br>if you intend to use all the CPUs or the full GPU.|
| kepler        | running simulations | manual submission| inform other before using.|

<br><br>
 
