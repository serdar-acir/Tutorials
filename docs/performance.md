[![Documentation Status](https://readthedocs.org/projects/su-hpc-tutorials/badge/?version=latest)](https://su-hpc-tutorials.readthedocs.io/en/latest/?badge=latest)
# Performans Optimization Tips
Defining performance in HPC platforms includes both the program execution in means of speed and the total wait time until your job is accepted for execution by the system.

For HPC environments performance optimization is probably the most important aspect after the proper functioning of the code. For example, sharing the same CPU cache for tasks that communicate with other may eliminate significant interconnect delays hence improving the performance. And separating independent tasks with a memory intensive workload onto separate sockets with a wider memory bandwidth may lead to performance improvements, leading to faster results. All these can be achieved by using appropriate workload scheduler commands for your own workload.

In this short article I will talk about a few Slurm commands that you can play with to minimize both the computation time and the wait time.


`** this article applies to linux batch scripts only`

Check if your tool is multi-threaded or not. If multi-threaded you probably will want to use the CPU cores on the same CPU, instead of separate CPUs, sockets or nodes.
For example to use all the 24 cores on a single CPU, on the command line use:

`--ntasks=1 --cpus-per-task=24`

,and in the batch script, this translates as:

`#SBATCH --tasks-per-node=1`

`#SBATCH --cpus-per-task=24`

This may delay the execution of your script if your demanded resources are not available. 
If multi-threaded and your tool scales well with the number of CPU cores, you may want to expand to the next available CPU on the same socket.
The default binding strategy of slurm is to expand to the next CPU, you can safely increase `--cpus-per-task`.
