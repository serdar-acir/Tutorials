# FENS HPC CLUSTER START GUIDE

## New User Warnings

- If you have never used a Cluster, or are not familiar with this cluster, YOU WILL WANT to read and follow the examples below to become familiar with how to run jobs on HPC. It is a common practice by new users to ignore this manual and simply try to run jobs without understanding what they are doing. Such carelessness can and WILL easily impact hundreds/thousands of critical jobs and users currently running on the cluster. If your actions compromise the health of the HPC cluster, your account will be LOCKED so please make sure you run through the examples below before you embark on running jobs.


- Do NOT use the login nodes for work. If everyone does this, the login nodes will crash keeping HPC users from being able to login to the cluster.

- Never submit large number of jobs (greater than 2) without first running a small test case to make sure all works as expected. Start slow and then ramp up with jobs once you are familiar with how things work.

- If you have a question, in the first instance please carefully check this User Guide.

## How to use HPC

Using a High Performance Computing Cluster such as the HPC Clusterrequires at a minimum some basic understanding of the [Linux Operating System.](https://www.google.com/url?q=http://en.wikipedia.org/wiki/Linux&sa=D&ust=1570008089847000)

It is outside the scope of this manual to explain Linux commands and/or how parallel programs such as MPI work. This manual simply explains how to run jobs on the HPC cluster.


When you login to HPC you are connected to what is called a login node. The HPC Cluster has several major components:

*   Login nodes
*   A Head node
*   Compute nodes



The head node runs all of the cluster critical services.



The login nodes are meant for simple tasks such as submitting jobs, checking on job status, editing (emacs, vi) and performing simple tasks.



The compute nodes are the workhorse of the cluster. For computational work both Serial or Parallel, in Batch mode or Interactive mode, you will be using the compute nodes.



## Getting started



You will need to have a basic understanding of Linux and Linux commands in order to use the system, unless you use an application that has a web or GUI interface to the compute resources.



HPC are shared resources that need to allocate user job requests amongst the available processors and memory in an equitable manner. This is done using a batch job queueing system and a job scheduler. HPC use the Torque queuing system which is based on PBS.



## How do I login to the HPC Machines?



### Windows



Use a secure shell client, e.g. [MobaXterm](https://www.google.com/url?q=https://mobaxterm.mobatek.net/features.html&sa=D&ust=1570008089849000)



1.  Here is the direct link to [download the mobaxterm program](https://www.google.com/url?q=http://mobaxterm.mobatek.net/download-home-edition.html&sa=D&ust=1570008089850000)
2.  Once you have mobaxterm installed [follow this guide](https://www.google.com/url?q=http://mobaxterm.mobatek.net/documentation.html&sa=D&ust=1570008089850000)

[](https://www.google.com/url?q=http://support.ersa.edu.au/hpc/tizard-putty.html&sa=D&ust=1570008089851000)

Note if you have cygwin installed, you can open a cygwin-terminal and then use ssh the same as for Linux and Mac below.



If you aren’t sure what cygwin is, you can safely ignore the above line.



### Linux and Mac



Use ssh on the command line



ssh username@IP

Note: Username is your HPC username



## How do I copy files/data to the HPC Machines?



### Windows



Use MobaXterm. This is a GUI-based scp client for MS Windows-based computers that has a  drag-and-drop facility and an inbuilt file editor. If you have cygwin installed, you can open a cygwin-terminal and then use ssh the same as Linux and Mac below.



*   [Download MobaXterm](https://www.google.com/url?q=http://mobaxterm.mobatek.net/documentation.html%232_3_3&sa=D&ust=1570008089852000)



### Linux and Mac



Use the scp on the command line



<span class="c7 c46">scp file-to-name USERNAME@IP<span class="c57 c46 c62 c7">:~/HOME_DIR/SUB_FOLDER/new-filename

This will copy the file to a SUB_FOLDER and renaming it to new-filename



## Now that I have connected to the HPC System - What do I do now



You need to use the Linux command line. Try this [cheat sheet](https://www.google.com/url?q=http://overapi.com/linux/&sa=D&ust=1570008089854000) to get you started.



## How do I edit my files on the HPC system?



Use a command line editor such as ‘vi’  or ‘emacs’. Here are some cheat notes to get you started:



*   [Vi cheat sheet](https://www.google.com/url?q=http://www.lagmonster.org/docs/vi.html&sa=D&ust=1570008089855000)
*   [UNIX tutorial for beginners](https://www.google.com/url?q=http://www.ee.surrey.ac.uk/Teaching/Unix/&sa=D&ust=1570008089855000)



## Home Folder



Home Folder is located at /cta/users/<username>/. This folder is for long term storage to keep your job files. It is a general purpose distributed file system.



## Application software



To see a list of application software that is installed on the HPC, type the the module avail command from your ssh console once you have logged in. This will give a list of applications, along with their version numbers.



If you want any other software installed, or a different version, send a request email [support@compecta.com](mailto:support@compecta.com). Please include a detailed information about the software like web page, version, license etc. Note that if the software requires a licence, the users of the software will need to purchase the licence.



Some software will only run on a single processor, in which case you will probably not see any speedup from running the software on the supercomputer compared to running it on your desktop, unless it requires large memory. However, many standard software packages can take advantage of multiple processors, or have parallel versions (e.g. using MPI) that can. Check the user guide for the software.



# SLURM queuing system



HPC that are shared among many users typically use a job management system such as Torque, SLURM, SGE or Moab to manage submission and execution of jobs.



Jobs are not run directly from the command line, the user needs to create a job script which specifies both the required compute resources, libraries and the job’s application that is to be run.



The script is submitted to the job management system (queueing system) and if the requested resources (processors, memory, etc) are available on the system, the job will by run.



If not, it will be placed in a queue until such time as the resources do become available. In order to provide a fair share of the resources among users, the priority of jobs in the queue may be varied based on how much resources someone has used, so it is possible that jobs may not run in the order in which they have been submitted to the queue.



Users wanting to use the HPC need to understand how to use the queueing system, how to create the job submission script, as well as check its progress or delete a job from the queueing system.



## Running jobs



Jobs are managed by a Resource Manager on the HPC Cluster. SABANCI HPC Cluster uses SLURM Resource Manager for this purpose.



You need to login (using ssh) to the HPC Cluster and submit jobs using sbatch command.



## SLURM Job Submission S



You will find SLURM submission script templates in a the folder: /cta/share/jobscripts



Copy the one you need to your work folder and modify it as required:



mkdir /cta/users/<username>/workfolder



cd /cta/users/<username>/workfolder/



cp /cta/share/jobscripts/example_submit.sh /cta/users/<username>/workfolder/my_experiment.sh



vim my_experiment.sh



## Submitting jobs to the queue



Jobs are submitted to the system with the command below:



`sbatch myscript.sh`



See the page about SLURM Queueing System Commands for more information on creating job submission scripts.



## SLURM Partitions (Job Queues)



SLURM Resource Manager has partitions which are job queues. These partitions has different limits and member nodes.



SABANCI HPC Cluster’s Partitions are listed below:



These partitions and limits are subject to change in near future. Please check back here again. You can also see the active partitions and their limits with sinfo command on the cluster.



## [The SLURM Cheat Sheet](https://www.google.com/url?q=https://slurm.schedmd.com/pdfs/summary.pdf&sa=D&ust=1570008089861000)



## Essential SLURM Commands

<table class="c52">

<tbody>

<tr class="c56">

<td class="c49 c68" colspan="1" rowspan="1">

<span class="c43 c40 c30 c39">Command

</td>

<td class="c16 c68" colspan="1" rowspan="1">

<span class="c43 c40 c30 c39">Description

</td>

</tr>

<tr class="c56">

<td class="c49" colspan="1" rowspan="1">

<span class="c40 c30 c55 c7">sbatch<span class="c7 c23">

<span class="c5">sbatch [script]

</td>

<td class="c16" colspan="1" rowspan="1">

<span class="c15 c7">Submit a batch job

<span class="c51 c7">
Example:<span class="c30 c7">
<span class="c5">$ sbatch job.sub

</td>

</tr>

<tr class="c56">

<td class="c49" colspan="1" rowspan="1">

<span class="c40 c30 c7 c55">scancel<span class="c23 c7">

<span class="c5">scancel [job_id]

</td>

<td class="c16" colspan="1" rowspan="1">

<span class="c30 c7">Kill a running job or cancel queued one
<span class="c51 c7">
Example:<span class="c30 c7">
<span class="c5">$ scancel 123456

</td>

</tr>

<tr class="c56">

<td class="c49" colspan="1" rowspan="1">

<span class="c40 c30 c55 c7">squeue<span class="c23 c7">

<span class="c5">squeue

</td>

<td class="c16" colspan="1" rowspan="1">

<span class="c30 c7">List running or pending jobs
<span class="c51 c7">
Example:<span class="c30 c7">
<span class="c5">$ squeue

</td>

</tr>

<tr class="c56">

<td class="c49" colspan="1" rowspan="1">

<span class="c40 c30 c55 c7">squeue -u userid<span class="c23 c7">

<span class="c5">squeue -u [userid]

</td>

<td class="c16" colspan="1" rowspan="1">

<span class="c7 c30">List running or pending jobs
<span class="c7 c51">
Example:<span class="c30 c7">
<span class="c5">$ squeue -u john

</td>

</tr>

</tbody>

</table>





## Submitting a SLURM Job Script



The job flags are used with SBATCH command.  The syntax for the SLURM directive in a script is  "#SBATCH <flag>".  Some of the flags are used with the srun and salloc commands, as well for interactive jobs.



<a id="t.3dfacbe3b6b4ac376d3dc1e2da925d8ec90b580e"></a><a id="t.1"></a>

<table class="c52">

<tbody>

<tr class="c61">

<td class="c38" colspan="1" rowspan="1">

<span class="c40 c30 c39">Resource

</td>

<td class="c59" colspan="1" rowspan="1">

<span class="c40 c30 c39">Flag Syntax

</td>

<td class="c19" colspan="1" rowspan="1">

<span class="c40 c30 c39">Description

</td>

<td class="c68 c82" colspan="1" rowspan="1">

<span class="c40 c30 c39">Notes

</td>

</tr>

<tr class="c10">

<td class="c75" colspan="1" rowspan="1">

<span class="c29 c7">partition

</td>

<td class="c88" colspan="1" rowspan="1">

<span class="c43 c45 c7">--partition=short

</td>

<td class="c87" colspan="1" rowspan="1">

<span class="c43 c45 c7">Partition is a queue for jobs.

</td>

<td class="c85" colspan="1" rowspan="1">

<span class="c43 c45 c7">default on

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">qos

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7"> --qos=short

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c7 c73">QOS is quality of service value<span class="c43 c45 c7"> (limits or priority boost)

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default on

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">time

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--time=01:00:00

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Time limit for the job.

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">1 hour; default is 2 hours

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">nodes

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--nodes=1

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Number of compute nodes for the job.

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default is 1

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">cpus/cores

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--ntasks-per-node=4

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Corresponds to number of cores on the compute node.

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default is 1

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">resource feature

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--gres=gpu:1

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Request use of GPUs on compute nodes

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default is no feature

</td>

</tr>

<tr class="c79">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">memory

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--mem=15500

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Memory limit per compute node for the  job.  Do not use with mem-per-cpu flag.

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default limit is 15500 MB per core in beegfs[101-108] nodes

</td>

</tr>

<tr class="c79">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">memory

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--mem-per-cpu=4000

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Per core memory limit.  Do not use the mem flag,

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default limit is 15500 MB per core in beegfs[101-108] nodes

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">account

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--account=users

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Users may belong to groups or accounts.

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default is the user's primary group.

</td>

</tr>

<tr class="c61">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">job name

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--job-name="hello_test"

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Name of job.

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default is the JobID

</td>

</tr>

<tr class="c61">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">constraint

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--constraint=gpu

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">compute-nodes

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">AVAIL_FEATURES

</td>

</tr>

<tr class="c61">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">output file

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--output=test.out

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Name of file for stdout.

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default is the JobID

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c7 c29">email address

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--mail-user=username@foo.com

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">User's email address

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c7 c45">required

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">email notification

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--mail-type=ALL

<span class="c43 c45 c7">--mail-type=END

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">When email is sent to user.

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">omit for no email

</td>

</tr>

</tbody>

</table>

## 

## Running a GUI on the Cluster (X11 Forwarding) (soon..)



Some applications provide the capability to interact with a graphical user interface (GUI). It is not typical of parallel jobs, but large-memory applications and computationally steered applications can offer such capability. With Slurm, once a resource allocation is granted for an interactive session (or a batch job when the submitting terminal if left logged in), we can use srun to provide X11 graphical forwarding all the way from the compute nodes to our desktop using srun --x11 



For example, to run an X terminal:



`srun --x11 -A users -p short -n1 --qos=users --pty $SHELL`

Note that the user must have X11 forwarded to the login node for this to work -- this can be checked by running xclock at the command line.

Additionally, the --x11argument can be augmented in this fashion --x11=[batch|first|last|all] to the following effects:

*   --x11=first This is the default, and provides X11 forwarding to the first compute hosts allocated.
*   --x11=last This provides X11 forwarding to the last of the compute hosts allocated.
*   --x11=all This provides X11 forwarding from all allocated compute hosts, which can be quite resource heavy and is an extremely rare use-case.
*   --x11=batch This supports use in a batch job submission, and will provide X11 forwarding to the first node allocated to a batch job. The user must leave open the X11 forwarded login node session where they submitted the job.

## Job Reason Codes



These codes identify the reason that a job is waiting for execution. A job may be waiting for more than one reason, in which case only one of those reasons is displayed.





<a id="t.9aa0fe54d84fd9007f94a96abe92ee9227ca6cfc"></a><a id="t.2"></a>

<table class="c52">

<tbody>

<tr class="c76">

<td class="c68 c86" colspan="1" rowspan="1">

<span class="c40 c39">State

</td>

<td class="c68 c81" colspan="1" rowspan="1">

<span class="c40 c39">Code

</td>

<td class="c33" colspan="1" rowspan="1">

<span class="c40 c39">Meaning

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">PENDING

</td>

<td class="c14" colspan="1" rowspan="1">

PD

</td>

<td class="c6" colspan="1" rowspan="1">

Job is awaiting resource allocation.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">RUNNING

</td>

<td class="c14" colspan="1" rowspan="1">

R

</td>

<td class="c6" colspan="1" rowspan="1">

Job currently has an allocation.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">SUSPENDED

</td>

<td class="c14" colspan="1" rowspan="1">

S

</td>

<td class="c6" colspan="1" rowspan="1">

Job has an allocation, but execution has been suspended.

</td>

</tr>

<tr class="c84">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">COMPLETING

</td>

<td class="c14" colspan="1" rowspan="1">

CG

</td>

<td class="c6" colspan="1" rowspan="1">

Job is in the process of completing. Some processes on some nodes may still be active.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">COMPLETED

</td>

<td class="c14" colspan="1" rowspan="1">

CD

</td>

<td class="c6" colspan="1" rowspan="1">

Job has terminated all processes on all nodes.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">CONFIGURING

</td>

<td class="c14" colspan="1" rowspan="1">

CF

</td>

<td class="c6" colspan="1" rowspan="1">

 Job has been allocated resources, but are waiting for them to become ready for use

</td>

</tr>

<tr class="c89">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">CANCELED

</td>

<td class="c14" colspan="1" rowspan="1">

CA

</td>

<td class="c6" colspan="1" rowspan="1">

Job was explicitly cancelled by the user or system administrator.

The job may or may not have been initiated.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">FAILED

</td>

<td class="c14" colspan="1" rowspan="1">

F

</td>

<td class="c6" colspan="1" rowspan="1">

Job terminated with non-zero exit code or other failure condition.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">TIMEOUT

</td>

<td class="c14" colspan="1" rowspan="1">

TO

</td>

<td class="c6" colspan="1" rowspan="1">

Job terminated upon reaching its time limit.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">PREEMPTED

</td>

<td class="c14" colspan="1" rowspan="1">

PR

</td>

<td class="c6" colspan="1" rowspan="1">

Job has been suspended by an higher priority job on the same ressource.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">NODE_FAIL

</td>

<td class="c14" colspan="1" rowspan="1">

NF

</td>

<td class="c6" colspan="1" rowspan="1">

Job terminated due to failure of one or more allocated nodes.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">InvalidQOS

</td>

<td class="c14" colspan="1" rowspan="1">



</td>

<td class="c6" colspan="1" rowspan="1">

The job's QOS is invalid.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">PartitionNodeLimit

</td>

<td class="c14" colspan="1" rowspan="1">



</td>

<td class="c6" colspan="1" rowspan="1">

The number of nodes required by this job is outside of it's partitions current limits. Can also indicate that required nodes are DOWN or DRAINED.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">PartitionTimeLimit

</td>

<td class="c14" colspan="1" rowspan="1">



</td>

<td class="c6" colspan="1" rowspan="1">

The job's time limit exceeds it's partition's current time limit.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">QOSJobLimit

</td>

<td class="c14" colspan="1" rowspan="1">



</td>

<td class="c6" colspan="1" rowspan="1">

The job's QOS has reached its maximum job count.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">QOSResourceLimit

</td>

<td class="c14" colspan="1" rowspan="1">



</td>

<td class="c6" colspan="1" rowspan="1">

The job's QOS has reached some resource limit.

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">QOSTimeLimit

</td>

<td class="c14" colspan="1" rowspan="1">



</td>

<td class="c6" colspan="1" rowspan="1">

The job's QOS has reached its time limit.

</td>

</tr>

</tbody>

</table>



Please follow the links for more...



[JOB REASON CODES](https://www.google.com/url?q=https://slurm.schedmd.com/squeue.html%23lbAF&sa=D&ust=1570008089914000)

[JOB STATE CODES](https://www.google.com/url?q=https://slurm.schedmd.com/squeue.html%23lbAG&sa=D&ust=1570008089914000)



## QoS settings





<a id="t.001774065333135c85f7249b6b7fd6da4434d52b"></a><a id="t.3"></a>

<table class="c52">

<tbody>

<tr class="c56">

<td class="c49 c68" colspan="1" rowspan="1">

<span class="c43 c40 c30 c39">Command

</td>

<td class="c16 c68" colspan="1" rowspan="1">

<span class="c43 c40 c30 c39">Description

</td>

</tr>

<tr class="c56">

<td class="c49" colspan="1" rowspan="1">

<span class="c40 c30 c55 c7 c57">users

<span class="c34 c7">MaxSubmitJobsPerUser=10

<span class="c34 c7">MaxTRES=cpu=40

<span class="c34 c7">MaxNodes=2

<span class="c34 c7">--account=users

<span class="c77 c51 c55 c7">--qos=short

</td>

<td class="c16" colspan="1" rowspan="1">

<span class="c15 c7">All users

<span class="c7 c15">All partitions

<span class="c43 c77 c51 c7">

</td>

</tr>

<tr class="c56">

<td class="c49" colspan="1" rowspan="1">

<span class="c57 c40 c30 c55 c7">cuda

<span class="c34 c7">MaxSubmitJobsPerUser=10

<span class="c34 c7">MaxTRES=cpu=40

<span class="c34 c7">MaxNodes=2

<span class="c34 c7">--account=cuda

<span class="c7 c34">--qos=cuda

<span class="c34 c7">--gres=gpu:1

</td>

<td class="c16" colspan="1" rowspan="1">

<span class="c15 c7">All users

<span class="c15 c7">Includes cuda partitions

<span class="c15 c7">

</td>

</tr>

</tbody>

</table>





# <span class="c43 c72 c40">Software



## System software



*   Ubuntu 16.04 LTS  - operating system
*   [SLURM resource manager](https://www.google.com/url?q=https://slurm.schedmd.com/&sa=D&ust=1570008089922000)



### Compilers and parallel programming libraries



*   GNU Compiler (GCC, GFortran)
*   Java, Python, Perl, Ruby
*   OpenMPI - library for MPI message passing for use in parallel programming over Infiniband and Ethernet
*   ...and more. We will be updating this document in future.

### 

### Libraries



*   Please run the module avail command from your ssh console to view a list of available applications.



### Application software



*   Gaussian, Blast, Namd, Gromacs and many more.
*   Please run the module avail command from your ssh console to view a list of available applications.





# Contacts and Help



For more information on HPC facilities, systems support, assistance with parallel programming and performance optimisation and to report any problems, contact the CompecTA Service Desk.

## Need Additional Help?

Alternatively you can sent an email to [support@compecta.com](mailto:support@compecta.com) this will create a support ticket automatically.



When reporting problems, please give as much information as you can to help us in diagnosis, for example:



*   Your username
*   Queue/partition name
*   Job ID(s)
*   A copy of any error messages
*   Command used to submit the job(s)
*   Path(s) to scripts called by the submission command
*   Path(s) to output files from your jobs
*   When the problem occurred
*   What commands or programs you were trying to execute at the time
*   A pointer to the program you were trying to run or compile



