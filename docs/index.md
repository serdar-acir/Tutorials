# FENS HPC CLUSTER START GUIDE

## Getting a Cluster Account  
In order to get an account in Tosun cluster, send an email to [support@compecta.com](mailto:support@compecta.com) along with the name of the professor you are working with since the accounts are created under groups of professors.  
  
CompectA support will provide a username and a password. Upon first login, change your password with `passwd` command.


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



Use `ssh` on the command line

If you are outside of the campus:  

`ssh username@flow.sabanciuniv.edu`  
Then  
`ssh username@IP`  
  
If you are in the campus:  
`ssh username@IP`

Note: Username is your HPC username



## How do I copy files/data to the HPC Machines?



### Windows



Use MobaXterm. This is a GUI-based scp client for MS Windows-based computers that has a  drag-and-drop facility and an inbuilt file editor. If you have cygwin installed, you can open a cygwin-terminal and then use ssh the same as Linux and Mac below.



*   [Download MobaXterm](https://www.google.com/url?q=http://mobaxterm.mobatek.net/documentation.html%232_3_3&sa=D&ust=1570008089852000)



### Linux and Mac



Use the scp on the command line



`scp file-to-name USERNAME@IP:~/HOME_DIR/SUB_FOLDER/new-filename`

This will copy the file to a **SUB_FOLDER** and renaming it to new-filename



## Now that I have connected to the HPC System - What do I do now



You need to use the Linux command line. Try this [cheat sheet](https://www.google.com/url?q=http://overapi.com/linux/&sa=D&ust=1570008089854000) to get you started.



## How do I edit my files on the HPC system?



Use a command line editor such as ‘vi’  or ‘emacs’. Here are some cheat notes to get you started:



*   [Vi cheat sheet](https://www.google.com/url?q=http://www.lagmonster.org/docs/vi.html&sa=D&ust=1570008089855000)
*   [UNIX tutorial for beginners](https://www.google.com/url?q=http://www.ee.surrey.ac.uk/Teaching/Unix/&sa=D&ust=1570008089855000)



## Home Folder



Home Folder is located at `/cta/users/username/`. This folder is for long term storage to keep your job files. It is a general purpose distributed file system.



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



Jobs are managed by a Resource Manager on the HPC Cluster. TOSUN and SUNUM clusters uses SLURM Resource Manager for this purpose.



You need to login (using ssh) to the HPC Cluster and submit jobs using sbatch command.





