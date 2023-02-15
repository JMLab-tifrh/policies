# Job script details for all HPCs
Here the details of the job scripts required for all HPCs have been compiled. Towards the end, a generic example has been provided which showcases how to block a complete node but run multiple simulations. 

## Job script syntax
### JMC
#### queue name: batch
```#!/bin/bash
#PBS -l nodes=1:ppn=32
#PBS -N po_start_s1
#PBS -q batch

cd /path/to/job/folder
module load /required/modules
```
#### queue name: sql
```#!/bin/bash
#PBS -l nodes=1:ppn=64
#PBS -N po_start_s1
#PBS -q sql

cd /path/to/job/folder
module load /required/modules 
```

### ryzencluster
#### queue name: ryzen9-3080
```#!/bin/bash
#PBS -l nodes=1:ppn=24
#PBS -N job-name
#PBS -q ryzen9-3080

cd $PBS_O_WORKDIR
module purge
module load /required/modules
```
#### queue name: ryzen9-2080
```#!/bin/bash
#PBS -l nodes=1:ppn=24
#PBS -N job-name
#PBS -q ryzen9-2080

cd $PBS_O_WORKDIR
module purge
module load /required/modules
```
#### queue name: ryzen7-3080
```#!/bin/bash
#PBS -l nodes=1:ppn=16
#PBS -N job-name
#PBS -q ryzen7-3080

cd $PBS_O_WORKDIR
module purge
module load /required/modules
```

### ampere
#### queue name: ryzen
```#!/bin/bash
#PBS -l select=1:ncpus=32
#PBS -N <job name>
#PBS -j oe
#PBS -q ryzen

cd $PBS_O_WORKDIR
module purge
module load /required/modules
```
#### queue name: epyc
```#!/bin/bash
#PBS -l select=1:ncpus=32
#PBS -N <job name>
#PBS -j oe
#PBS -q epyc

cd $PBS_O_WORKDIR
module purge
module load /required/modules
```

### karplus
#### queue name: workq
```#!/bin/bash
#PBS -l select=1:ncpus=32
#PBS -N <job name>
#PBS -j oe
#PBS -q workq

cd $PBS_O_WORKDIR
module purge
module load /required/modules
```

## Example job scripts
### submit jobs using all CPUs of a node
Let the number of CPUs be 32 per node and each node has 2 GPUs. I want to submit a job using all 32 cpus and both GPUs.
```#!/bin/bash
#PBS -l select=1:ncpus=32
#PBS -N <job name>
#PBS -j oe
#PBS -q <queue name>

cd $PBS_O_WORKDIR
module purge
module load gromacs2022

export OMP_NUM_THREADS=32

gmx mdrun -ntmpi 1 -ntomp 32 -v -deffnm run -gpu_id 0,1 >& log_mdrun_run &
wait
```
### submit multiple simulations in a single jobs using all CPUs of a node
Let the number of CPUs be 32 per node and each node has 2 GPUs. I want 4 simulations, each running on 8 CPUs and divided between 2 GPUs equally.
```#!/bin/bash
#PBS -l select=1:ncpus=32
#PBS -N <job name>
#PBS -j oe
#PBS -q <queue name>

cd $PBS_O_WORKDIR
module purge
module load gromacs2022

export OMP_NUM_THREADS=8

gmx mdrun -ntmpi 1 -ntomp 8 -v -deffnm run1 -gpu_id 0 >& log_mdrun_run1 &
gmx mdrun -ntmpi 1 -ntomp 8 -v -deffnm run2 -gpu_id 0 >& log_mdrun_run2 &
gmx mdrun -ntmpi 1 -ntomp 8 -v -deffnm run3 -gpu_id 1 >& log_mdrun_run3 &
gmx mdrun -ntmpi 1 -ntomp 8 -v -deffnm run4 -gpu_id 1 >& log_mdrun_run4 &
wait
```
