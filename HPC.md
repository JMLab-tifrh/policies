# Job submission policies
This is the documentation for job submission policies for the HPCs exclusive to the group members.

## List and details of resources
### HPCs
| name | CPU model(s) | Num of CPUs per node | GPU model(s) | Num of GPUs per node | RAM per node (G)|
|:----:|:------------:|:--------------------:|:------------:|:--------------------:|:-----------:|
| JMC  | Intel(R) Xeon(R) CPU E5-2667v4 @ 3.20GHz <br>Intel(R) Xeon(R) Gold 6130 CPU @ 2.10GHz  | 32 or 64| Mixture of GTX 1080 and RTX 3080 | 2 GTX 1080s or 1 RTX 3080 | 64 |
| ryzencluster | AMD Ryzen 9 3900X 12-Core Processor <br>AMD Ryzen 7 3800X 8-Core Processor | 24 or 16 | RTX 3080 | 1 RTX series GPU | 32 |
| ampere | AMD Ryzen Threadripper PRO 3955WX 16-Cores<br>AMD EPYC 7502P 32-Core Processor| 32 or 64 | RTX 3080 | 2 RTX 3080 | 32 or 64 |
| karplus | AMD Ryzen 9 5950X 16-Core Processor | 32 | RTX 3080 | 1 RTX 3080 | 32 |

### Single node servers
| name | CPU model(s) | Num of CPUs | GPU model(s) | Num of GPUs | RAM (G)|
|:----:|:------------:|:--------------------:|:------------:|:--------------------:|:-----------:|
| pascal | Intel(R) Xeon(R) CPU E5-2640 v3 @ 2.60GHz | 32 | GTX 980 Ti | 1 | 32 |
| maxwell2| Intel(R) Xeon(R) CPU E5-2640 v3 @ 2.60GHz | 32 | GTX 980 Ti | 8 | 64 |
| kepler | Intel(R) Xeon(R) CPU E5-2640 v4 @ 2.40GHz | 40 | Tesla K80 | 4 | 64 | 
| north  | Intel(R) Xeon(R) Gold 6130 CPU @ 2.10GHz | 32 | ---- | 0 | 128 |
| turing | AMD Ryzen Threadripper PRO 5975WX 32-Cores | 64 | RTX A5000 | 1 | 256 |

<br>

## general submission rules
<ol>
  <li> Always allocate the complete node for a single job submission. Since all simulations are always run on multiple seeds, multiple simulations, if needed, are to be run inside a single job script. An example has been provided later.</li>
  <li> Except, JMC, all other clusters have a maximum walltime (runtime) of 7 days (168 hrs). </li> 
  <li> It is advised to optimize the number of CPUs needed per simulation prior to longer runs. This ensures optimal usage of the computers. </li>
  <li> It is requested that users should output their trajectories in .xtc formats, unless explicitly needed, to reduce the storage space usage. Optionally, one should also output only the particles/atoms/groups which they would require. This would further reduce the storage space needed. </li>
  <li> Take regular backups and do not use the HPC's storage for storing data. The HPCs have limited storage space and its complete utilization is highly likely to cause a system crash. </li>
  <li> Each HPC has its own job submission limit which has been detailed in later sections. Please abide by those rules. In case of any special requirement, JM's authorization will be needed. The person should also let others know about this so as to avoid any unnecessary misunderstandings and clashes.
</ol>

<br>

## Details of maximum usage limit for each HPC:
| HPC name   | maximum submission limit per queue  |
|:----------:|-------------------------------------|
|JMC         |_sql_: 2 running (10 days maximum runtime)<br>_batch_: 5 running (2 days runtime)<br>_batch1_: 2 running on jm4 and jm5 (10 days runtime)|
|ryzencluster|_ryzen9-3080_: 4 running + 1 queue = 5<br>_ryzen7-3080_: 1 running + 1 queue = 2<br>_ryzen9-2080_: 2 running + 1 queue = 3|
|ampere      |_ryzen_: 9 running + 2 queue = 11<br>epyc: 1/2 running + 1 queue=2/3|
|karplus     |_workq_: 8 running + 2 queue = 10|

<br>

## Using single node (scheduler less) computers
| computer name | usage type          | submission type  | policy                    |
|:-------------:|---------------------|------------------|---------------------------|
| maxwell2      | running simulations | manual submission| inform other before using.|
| pascal        | running simulations | manual submission| inform other before using.|
| north         | analysis only       | manual submission| use if CPUs are free. Please inform everyone<br>if you intend to use all the CPUs together.|
| turing        | ML, analysis        | manual submission| use if CPUs and GPU are free. Please inform everyone<br>if you intend to use all the CPUs or the full GPU.|
| kepler        | running simulations | manual submission| inform other before using.|
