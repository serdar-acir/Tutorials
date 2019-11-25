# <span class="c43 c40 c72">FENS HPC CLUSTER START GUIDE</span>

<span class="c2"></span>

<span class="c11">[FENS HPC CLUSTER START GUIDE](#h.9ftmjcytp30d)</span>

<span class="c11">[RUNNING JOBS ON THE HPC CLUSTER](#h.cvbkf7dm8vxj)</span>

<span class="c11">[New User Warnings](#h.oe95zd2n47l9)</span>

<span class="c11">[How to use HPC](#h.52fo2fiyg120)</span>

<span class="c11">[Getting started](#h.gqhs5i5uuinv)</span>

<span class="c11">[How do I login to the HPC Machines?](#h.p3tmxkpdxjsz)</span>

<span class="c11">[Windows](#h.mmdli6988y6q)</span>

<span class="c11">[Linux and Mac](#h.y6bb2bqvafv9)</span>

<span class="c11">[How do I copy files/data to the HPC Machines?](#h.qq9l3mszkahp)</span>

<span class="c11">[Windows](#h.mj839yua4mwy)</span>

<span class="c11">[Linux and Mac](#h.dm9262kanstg)</span>

<span class="c11">[Now that I have connected to the HPC System - What do I do now](#h.xbdi19e18pd2)</span>

<span class="c11">[How do I edit my files on the HPC system?](#h.6q8gerwhti6e)</span>

<span class="c11">[Home Folder](#h.co80l0gyw9ll)</span>

<span class="c11">[Application software](#h.6c0cs8g08om8)</span>

<span class="c11">[SLURM queuing system](#h.41c5o4eezzxz)</span>

<span class="c11">[Running jobs](#h.46g2bom6qnyo)</span>

<span class="c11">[SLURM Job Submission Scripts](#h.2wsj7lu44j1q)</span>

<span class="c11">[Submitting jobs to the queue](#h.w6d13v6mxlu8)</span>

<span class="c11">[SLURM Partitions (Job Queues)](#h.ai2kkb1f9pro)</span>

<span class="c11">[The SLURM Cheat Sheet](#h.sbbrdnyyqxnf)</span>

<span class="c11">[Essential SLURM Commands](#h.mrclqhac6crp)</span>

<span class="c11">[Submitting a SLURM Job Script](#h.as26b1x8a22q)</span>

<span class="c11">[Running a GUI on the Cluster (X11 Forwarding) (soon..)](#h.k1vgovt7os06)</span>

<span class="c11">[Job Reason Codes](#h.9rihdooe2flq)</span>

<span class="c11">[QoS settings](#h.2ppentf04rrq)</span>

<span class="c11">[Software](#h.halb8ljf6ta8)</span>

<span class="c11">[System software](#h.w3vlpavewqqc)</span>

<span class="c11">[Compilers and parallel programming libraries](#h.jg5wd0i1grxc)</span>

<span class="c11">[Libraries](#h.kyeztaq8rsh7)</span>

<span class="c11">[Application software](#h.cf29vkg8j1i3)</span>

<span class="c11">[Contacts and Help](#h.l6sy3zt7dowx)</span>

<span class="c11">[Need Additional Help?](#h.x48jap4y8k9u)</span>

<span class="c2"></span>

# <span class="c43 c72 c40">RUNNING JOBS ON THE HPC CLUSTER</span>

<span class="c2"></span>

## <span class="c43 c40 c71 c78">New User Warnings</span>

<span class="c2"></span>

<span class="c0">If you have never used a Cluster, or are not familiar with this cluster, YOU WILL WANT to read and follow the examples below to become familiar with how to run jobs on HPC. It is a common practice by new users to ignore this manual and simply try to run jobs without understanding what they are doing. Such carelessness can and WILL easily impact hundreds/thousands of critical jobs and users currently running on the cluster. If your actions compromise the health of the HPC cluster, your account will be LOCKED so please make sure you run through the examples below before you embark on running jobs.</span>

<span class="c0"></span>

<span class="c0">Do NOT use the login nodes for work. If everyone does this, the login nodes will crash keeping HPC users from being able to login to the cluster.</span>

<span class="c0"></span>

<span class="c0">Never submit large number of jobs (greater than 2) without first running a small test case to make sure all works as expected. Start slow and then ramp up with jobs once you are familiar with how things work.</span>

<span class="c0"></span>

<span class="c0">If you have a question, in the first instance please carefully check this User Guide.</span>

<span class="c0"></span>

## <span class="c43 c40 c63">How to use HPC</span>

<span class="c2"></span>

<span class="c7">Using a High Performance Computing Cluster such as the</span> <span class="c7">HPC Cluster</span><span class="c7">requires at a minimum some basic understanding of the</span> <span class="c53">[Linux Operating System.](https://www.google.com/url?q=http://en.wikipedia.org/wiki/Linux&sa=D&ust=1570008089847000)</span>

<span class="c43 c48 c71"></span>

<span class="c0">It is outside the scope of this manual to explain Linux commands and/or how parallel programs such as MPI work. This manual simply explains how to run jobs on the HPC cluster.</span>

<span class="c0"></span>

<span class="c7">When you login to</span> <span>HPC</span><span class="c0"> you are connected to what is called a login node. The HPC Cluster has several major components:</span>

<span class="c0"></span>

*   <span class="c0">Login nodes</span>
*   <span class="c0">A Head node</span>
*   <span class="c2">Compute nodes</span>

<span class="c2"></span>

<span class="c7">The</span> <span class="c40">head</span> <span class="c7 c40">node</span><span class="c0"> runs all of the cluster critical services.</span>

<span class="c0"></span>

<span class="c7">The login nodes are meant for simple tasks such as submitting jobs, checking on job status, editing</span> <span class="c42">(emacs, vi)</span><span class="c0"> and performing simple tasks.</span>

<span class="c0"></span>

<span class="c7">The</span> <span class="c40">compute</span> <span class="c40">nodes</span><span class="c0"> are the workhorse of the cluster. For computational work both Serial or Parallel, in Batch mode or Interactive mode, you will be using the compute nodes.</span>

<span class="c0"></span>

## <span class="c43 c44 c40">Getting started</span>

<span class="c2"></span>

<span class="c0">You will need to have a basic understanding of Linux and Linux commands in order to use the system, unless you use an application that has a web or GUI interface to the compute resources.</span>

<span class="c0"></span>

<span class="c0">HPC are shared resources that need to allocate user job requests amongst the available processors and memory in an equitable manner. This is done using a batch job queueing system and a job scheduler. HPC use the Torque queuing system which is based on PBS.</span>

<span class="c0"></span>

## <span class="c43 c44 c40">How do I login to the HPC Machines?</span>

<span class="c2"></span>

### <span class="c43 c40 c30 c83">Windows</span>

<span class="c2"></span>

<span class="c7">Use a secure shell client, e.g.</span> <span class="c53">[MobaXterm](https://www.google.com/url?q=https://mobaxterm.mobatek.net/features.html&sa=D&ust=1570008089849000)</span>

<span class="c0"></span>

1.  <span class="c7">Here is the direct link to</span> <span class="c53">[download the mobaxterm program](https://www.google.com/url?q=http://mobaxterm.mobatek.net/download-home-edition.html&sa=D&ust=1570008089850000)</span>
2.  <span class="c7">Once you have mobaxterm installed</span> <span class="c53">[follow this guide](https://www.google.com/url?q=http://mobaxterm.mobatek.net/documentation.html&sa=D&ust=1570008089850000)</span>

<span class="c11">[](https://www.google.com/url?q=http://support.ersa.edu.au/hpc/tizard-putty.html&sa=D&ust=1570008089851000)</span>

<span class="c42 c7">Note</span><span class="c0"> if you have cygwin installed, you can open a cygwin-terminal and then use ssh the same as for Linux and Mac below.</span>

<span class="c0"></span>

<span class="c0">If you aren’t sure what cygwin is, you can safely ignore the above line.</span>

<span class="c0"></span>

### <span class="c43 c40 c30 c50">Linux and Mac</span>

<span class="c2"></span>

<span class="c0">Use ssh on the command line</span>

<span class="c0"></span>

<span class="c46 c7">ssh username@IP
</span><span class="c7">
</span><span class="c7">Note:</span><span class="c0"> Username is your HPC username</span>

<span class="c0"></span>

## <span class="c43 c44 c40">How do I copy files/data to the HPC Machines?</span>

<span class="c2"></span>

### <span class="c43 c40 c30 c50">Windows</span>

<span class="c2"></span>

<span class="c0">Use MobaXterm. This is a GUI-based scp client for MS Windows-based computers that has a  drag-and-drop facility and an inbuilt file editor. If you have cygwin installed, you can open a cygwin-terminal and then use ssh the same as Linux and Mac below.</span>

<span class="c0"></span>

*   <span class="c53">[Download MobaXterm](https://www.google.com/url?q=http://mobaxterm.mobatek.net/documentation.html%232_3_3&sa=D&ust=1570008089852000)</span>

<span class="c2"></span>

### <span class="c43 c40 c50 c62">Linux and Mac</span>

<span class="c2"></span>

<span class="c0">Use the scp on the command line</span>

<span class="c0"></span>

<span class="c7 c46">scp file-to-name</span> <span class="c46 c7">USERNAME@IP</span><span class="c57 c46 c62 c7">:~/HOME_DIR/SUB_FOLDER/new-filename</span>

<span class="c7">This will</span> <span class="c0">copy the file to a SUB_FOLDER and renaming it to new-filename</span>

<span class="c0"></span>

## <span class="c43 c44 c40">Now that I have connected to the HPC System - What do I do now</span>

<span class="c2"></span>

<span class="c7">You need to use the Linux command line. Try this</span> <span class="c53">[cheat sheet](https://www.google.com/url?q=http://overapi.com/linux/&sa=D&ust=1570008089854000)</span><span> </span><span class="c0">to get you started.</span>

<span class="c0"></span>

## <span class="c43 c44 c40">How do I edit my files on the HPC system?</span>

<span class="c2"></span>

<span class="c0">Use a command line editor such as ‘vi’  or ‘emacs’. Here are some cheat notes to get you started:</span>

<span class="c2"></span>

*   <span class="c53">[Vi cheat sheet](https://www.google.com/url?q=http://www.lagmonster.org/docs/vi.html&sa=D&ust=1570008089855000)</span>
*   <span class="c53">[UNIX tutorial for beginners](https://www.google.com/url?q=http://www.ee.surrey.ac.uk/Teaching/Unix/&sa=D&ust=1570008089855000)</span>

<span class="c2"></span>

## <span>Home Folder</span>

<span class="c2"></span>

<span>Home Folder is located at</span> <span class="c40 c7">/cta/users/<username>/</span><span class="c0">. This folder is for long term storage to keep your job files. It is a general purpose distributed file system.</span>

<span class="c0"></span>

## <span class="c43 c44 c40">Application software</span>

<span class="c2"></span>

<span class="c7">To see a list of application software that is installed on the HPC, type the the</span><span class="c71"> </span><span class="c40 c7">module avail</span><span class="c0"> command from your ssh console once you have logged in. This will give a list of applications, along with their version numbers.</span>

<span class="c0"></span>

<span class="c7">If you want any other software installed, or a different version, send a request email</span> <span class="c53">[support@compecta.com](mailto:support@compecta.com)</span><span class="c0">. Please include a detailed information about the software like web page, version, license etc. Note that if the software requires a licence, the users of the software will need to purchase the licence.</span>

<span class="c0"></span>

<span class="c0">Some software will only run on a single processor, in which case you will probably not see any speedup from running the software on the supercomputer compared to running it on your desktop, unless it requires large memory. However, many standard software packages can take advantage of multiple processors, or have parallel versions (e.g. using MPI) that can. Check the user guide for the software.</span>

<span class="c0"></span>

# <span class="c54 c40">SLURM</span><span class="c43 c54 c40"> queuing system</span>

<span class="c2"></span>

<span class="c0">HPC that are shared among many users typically use a job management system such as Torque, SLURM, SGE or Moab to manage submission and execution of jobs.</span>

<span class="c0"></span>

<span class="c0">Jobs are not run directly from the command line, the user needs to create a job script which specifies both the required compute resources, libraries and the job’s application that is to be run.</span>

<span class="c0"></span>

<span class="c0">The script is submitted to the job management system (queueing system) and if the requested resources (processors, memory, etc) are available on the system, the job will by run.</span>

<span class="c0"></span>

<span class="c0">If not, it will be placed in a queue until such time as the resources do become available. In order to provide a fair share of the resources among users, the priority of jobs in the queue may be varied based on how much resources someone has used, so it is possible that jobs may not run in the order in which they have been submitted to the queue.</span>

<span class="c0"></span>

<span class="c0">Users wanting to use the HPC need to understand how to use the queueing system, how to create the job submission script, as well as check its progress or delete a job from the queueing system.</span>

<span class="c0"></span>

## <span class="c44 c40">Running jobs</span>

<span class="c0"></span>

<span class="c7">Jobs are managed by a Resource Manager on the HPC Cluster. SABANCI HPC Cluster uses SLURM Resource Manager for this purpose.</span>

<span class="c0"></span>

<span class="c7">You need to login (using ssh) to the HPC Cluster and submit jobs using</span> <span class="c40 c66 c7">sbatch</span><span class="c0"> command.</span>

<span class="c0"></span>

## <span class="c44 c40">SLURM Job</span> <span>S</span><span class="c44 c40">ubmission</span> <span>S</span><span class="c43 c40 c44">cripts</span>

<span class="c2"></span>

<span class="c7">You will find SLURM submission script templates in a the folder:</span> <span class="c40 c66 c7">/cta/share/jobscripts</span>

<span class="c0"></span>

<span class="c0">Copy the one you need to your work folder and modify it as required:</span>

<span class="c0"></span>

<span class="c57 c51 c40 c66 c7">mkdir /cta/users/<username>/workfolder</span>

<span class="c57 c51 c40 c7 c66"></span>

<span class="c57 c51 c40 c66 c7">cd /cta/users/<username>/workfolder/</span>

<span class="c57 c51 c40 c66 c7"></span>

<span class="c57 c51 c40 c66 c7">cp /cta/share/jobscripts/example_submit.sh /cta/users/<username>/workfolder/my_experiment.sh</span>

<span class="c57 c51 c40 c66 c7"></span>

<span class="c57 c51 c40 c66 c7">vim my_experiment.sh</span>

<span class="c5 c40 c43"></span>

## <span class="c43 c44 c40">Submitting jobs to the queue</span>

<span class="c2"></span>

<span class="c0">Jobs are submitted to the system with the command below:</span>

<span class="c0"></span>

<span class="c5 c40">sbatch</span><span class="c43 c5 c40"> myscript.sh</span>

<span class="c43 c5 c40"></span>

<span class="c43 c5 c77">See the page about SLURM Queueing System Commands for more information on creating job submission scripts.</span>

<span class="c43 c5 c77"></span>

## <span class="c43 c44 c40">SLURM Partitions (Job Queues)</span>

<span class="c2"></span>

<span class="c2">SLURM Resource Manager has partitions which are job queues. These partitions has different limits and member nodes.</span>

<span class="c2"></span>

<span class="c43 c40 c50 c62">SABANCI HPC Cluster’s Partitions are listed below:</span>

<span class="c2"></span>

<span>These partitions and limits are subject to change in near future. Please check back here again. You can also see the active partitions and their limits with</span> <span class="c40 c55">sinfo</span><span class="c2"> command on the cluster.</span>

<span class="c43 c5 c77"></span>

## <span class="c53 c40 c78">[The SLURM Cheat Sheet](https://www.google.com/url?q=https://slurm.schedmd.com/pdfs/summary.pdf&sa=D&ust=1570008089861000)</span>

<span class="c2"></span>

## <span class="c43 c44 c40">Essential SLURM Commands</span>

<span class="c43 c40 c30 c7"></span>

<a id="t.8b1832ee64848e9a1af3a8113e6b9e0a679bbd60"></a><a id="t.0"></a>

<table class="c52">

<tbody>

<tr class="c56">

<td class="c49 c68" colspan="1" rowspan="1">

<span class="c43 c40 c30 c39">Command</span>

</td>

<td class="c16 c68" colspan="1" rowspan="1">

<span class="c43 c40 c30 c39">Description</span>

</td>

</tr>

<tr class="c56">

<td class="c49" colspan="1" rowspan="1">

<span class="c40 c30 c55 c7">sbatch</span><span class="c7 c23">

</span><span class="c5">sbatch [script]</span>

</td>

<td class="c16" colspan="1" rowspan="1">

<span class="c15 c7">Submit a batch job</span>

<span class="c51 c7">
Example:</span><span class="c30 c7">
</span><span class="c5">$ sbatch job.sub</span>

</td>

</tr>

<tr class="c56">

<td class="c49" colspan="1" rowspan="1">

<span class="c40 c30 c7 c55">scancel</span><span class="c23 c7">

</span><span class="c5">scancel [job_id]</span>

</td>

<td class="c16" colspan="1" rowspan="1">

<span class="c30 c7">Kill a running job or cancel queued one
</span><span class="c51 c7">
Example:</span><span class="c30 c7">
</span><span class="c5">$ scancel 123456</span>

</td>

</tr>

<tr class="c56">

<td class="c49" colspan="1" rowspan="1">

<span class="c40 c30 c55 c7">squeue</span><span class="c23 c7">

</span><span class="c5">squeue</span>

</td>

<td class="c16" colspan="1" rowspan="1">

<span class="c30 c7">List running or pending jobs
</span><span class="c51 c7">
Example:</span><span class="c30 c7">
</span><span class="c5">$ squeue</span>

</td>

</tr>

<tr class="c56">

<td class="c49" colspan="1" rowspan="1">

<span class="c40 c30 c55 c7">squeue -u userid</span><span class="c23 c7">

</span><span class="c5">squeue -u [userid]</span>

</td>

<td class="c16" colspan="1" rowspan="1">

<span class="c7 c30">List running or pending jobs
</span><span class="c7 c51">
Example:</span><span class="c30 c7">
</span><span class="c5">$ squeue -u john</span>

</td>

</tr>

</tbody>

</table>

<span class="c43 c5 c77"></span>

<span class="c43 c5 c77"></span>

## <span class="c43 c44 c40">Submitting a SLURM Job Script</span>

<span class="c2"></span>

<span class="c0">The job flags are used with SBATCH command.  The syntax for the SLURM directive in a script is  "#SBATCH <flag>".  Some of the flags are used with the srun and salloc commands, as well for interactive jobs.</span>

<span class="c43 c5 c77"></span>

<a id="t.3dfacbe3b6b4ac376d3dc1e2da925d8ec90b580e"></a><a id="t.1"></a>

<table class="c52">

<tbody>

<tr class="c61">

<td class="c38" colspan="1" rowspan="1">

<span class="c40 c30 c39">Resource</span>

</td>

<td class="c59" colspan="1" rowspan="1">

<span class="c40 c30 c39">Flag Syntax</span>

</td>

<td class="c19" colspan="1" rowspan="1">

<span class="c40 c30 c39">Description</span>

</td>

<td class="c68 c82" colspan="1" rowspan="1">

<span class="c40 c30 c39">Notes</span>

</td>

</tr>

<tr class="c10">

<td class="c75" colspan="1" rowspan="1">

<span class="c29 c7">partition</span>

</td>

<td class="c88" colspan="1" rowspan="1">

<span class="c43 c45 c7">--partition=short</span>

</td>

<td class="c87" colspan="1" rowspan="1">

<span class="c43 c45 c7">Partition is a queue for jobs.</span>

</td>

<td class="c85" colspan="1" rowspan="1">

<span class="c43 c45 c7">default on</span>

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">qos</span>

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7"> --qos=short</span>

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c7 c73">QOS is quality of service value</span><span class="c43 c45 c7"> (limits or priority boost)</span>

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default on</span>

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">time</span>

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--time=01:00:00</span>

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Time limit for the job.</span>

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">1 hour; default is 2 hours</span>

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">nodes</span>

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--nodes=1</span>

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Number of compute nodes for the job.</span>

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default is 1</span>

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">cpus/cores</span>

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--ntasks-per-node=4</span>

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Corresponds to number of cores on the compute node.</span>

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default is 1</span>

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">resource feature</span>

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--gres=gpu:1</span>

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Request use of GPUs on compute nodes</span>

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default is no feature</span>

</td>

</tr>

<tr class="c79">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">memory</span>

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--mem=15500</span>

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Memory limit per compute node for the  job.  Do not use with mem-per-cpu flag.</span>

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default limit is 15500 MB per core in beegfs[101-108] nodes</span>

</td>

</tr>

<tr class="c79">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">memory</span>

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--mem-per-cpu=4000</span>

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Per core memory limit.  Do not use the mem flag,</span>

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default limit is 15500 MB per core in beegfs[101-108] nodes</span>

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">account</span>

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--account=users</span>

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Users may belong to groups or accounts.</span>

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default is the user's primary group.</span>

</td>

</tr>

<tr class="c61">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">job name</span>

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--job-name="hello_test"</span>

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Name of job.</span>

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default is the JobID</span>

</td>

</tr>

<tr class="c61">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">constraint</span>

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--constraint=gpu</span>

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">compute-nodes</span>

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">AVAIL_FEATURES</span>

</td>

</tr>

<tr class="c61">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">output file</span>

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--output=test.out</span>

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">Name of file for stdout.</span>

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">default is the JobID</span>

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c7 c29">email address</span>

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--mail-user=username@foo.com</span>

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">User's email address</span>

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c7 c45">required</span>

</td>

</tr>

<tr class="c10">

<td class="c37" colspan="1" rowspan="1">

<span class="c29 c7">email notification</span>

</td>

<td class="c35" colspan="1" rowspan="1">

<span class="c43 c45 c7">--mail-type=ALL</span>

<span class="c43 c45 c7">--mail-type=END</span>

</td>

<td class="c1" colspan="1" rowspan="1">

<span class="c43 c45 c7">When email is sent to user.</span>

</td>

<td class="c27" colspan="1" rowspan="1">

<span class="c43 c45 c7">omit for no email</span>

</td>

</tr>

</tbody>

</table>

## <span class="c43 c44 c40"></span>

## <span class="c43 c44 c40">Running a GUI on the Cluster (X11 Forwarding) (soon..)</span>

<span class="c2"></span>

<span class="c2">Some applications provide the capability to interact with a graphical user interface (GUI). It is not typical of parallel jobs, but large-memory applications and computationally steered applications can offer such capability. With Slurm, once a resource allocation is granted for an interactive session (or a batch job when the submitting terminal if left logged in), we can use srun to provide X11 graphical forwarding all the way from the compute nodes to our desktop using srun --x11 <application>.</span>

<span class="c2"></span>

<span class="c2">For example, to run an X terminal:</span>

<span class="c2"></span>

<span class="c57 c45 c41 c58">srun --x11 -A users -p short -n1 --qos=users --pty $SHELL</span>

<span class="c41">Note that the user must have X11 forwarded to the login node for this to work -- this can be checked by running</span> <span class="c41 c42">xclock</span><span class="c43 c48 c41"> at the command line.</span>

<span class="c41">Additionally, the</span> <span class="c41 c42">--x11</span><span class="c41">argument can be augmented in this fashion</span> <span class="c41 c42">--x11=[batch|first|last|all]</span><span class="c43 c48 c41"> to the following effects:</span>

*   <span class="c41 c42">--x11=first</span> <span class="c43 c41 c48">This is the default, and provides X11 forwarding to the first compute hosts allocated.</span>
*   <span class="c41 c42">--x11=last</span><span class="c43 c48 c41"> This provides X11 forwarding to the last of the compute hosts allocated.</span>
*   <span class="c41 c42">--x11=all</span><span class="c43 c48 c41"> This provides X11 forwarding from all allocated compute hosts, which can be quite resource heavy and is an extremely rare use-case.</span>
*   <span class="c41 c42">--x11=batch</span><span class="c41"> This supports use in a batch job submission, and will provide X11 forwarding to the first node allocated to a batch job. The user must leave open the X11 forwarded login node session where they submitted the job.</span>

## <span>J</span><span class="c43 c44 c40">ob Reason Codes</span>

<span class="c2"></span>

<span class="c0">These codes identify the reason that a job is waiting for execution. A job may be waiting for more than one reason, in which case only one of those reasons is displayed.</span>

<span class="c0"></span>

<span class="c0"></span>

<a id="t.9aa0fe54d84fd9007f94a96abe92ee9227ca6cfc"></a><a id="t.2"></a>

<table class="c52">

<tbody>

<tr class="c76">

<td class="c68 c86" colspan="1" rowspan="1">

<span class="c40 c39">State</span>

</td>

<td class="c68 c81" colspan="1" rowspan="1">

<span class="c40 c39">Code</span>

</td>

<td class="c33" colspan="1" rowspan="1">

<span class="c40 c39">Meaning</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">PENDING</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2">PD</span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">Job is awaiting resource allocation.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">RUNNING</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2">R</span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">Job currently has an allocation.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">SUSPENDED</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2">S</span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">Job has an allocation, but execution has been suspended.</span>

</td>

</tr>

<tr class="c84">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">COMPLETING</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2">CG</span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">Job is in the process of completing. Some processes on some nodes may still be active.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">COMPLETED</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2">CD</span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">Job has terminated all processes on all nodes.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">CONFIGURING</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2">CF</span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2"> Job has been allocated resources, but are waiting for them to become ready for use</span>

</td>

</tr>

<tr class="c89">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">CANCELED</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2">CA</span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">Job was explicitly cancelled by the user or system administrator.</span>

<span class="c2">The job may or may not have been initiated.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">FAILED</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2">F</span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">Job terminated with non-zero exit code or other failure condition.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">TIMEOUT</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2">TO</span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">Job terminated upon reaching its time limit.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">PREEMPTED</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2">PR</span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">Job has been suspended by an higher priority job on the same ressource.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">NODE_FAIL</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2">NF</span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">Job terminated due to failure of one or more allocated nodes.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">InvalidQOS</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2"></span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">The job's QOS is invalid.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">PartitionNodeLimit</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2"></span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">The number of nodes required by this job is outside of it's partitions current limits. Can also indicate that required nodes are DOWN or DRAINED.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">PartitionTimeLimit</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2"></span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">The job's time limit exceeds it's partition's current time limit.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">QOSJobLimit</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2"></span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">The job's QOS has reached its maximum job count.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">QOSResourceLimit</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2"></span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">The job's QOS has reached some resource limit.</span>

</td>

</tr>

<tr class="c20">

<td class="c8" colspan="1" rowspan="1">

<span class="c26">QOSTimeLimit</span>

</td>

<td class="c14" colspan="1" rowspan="1">

<span class="c2"></span>

</td>

<td class="c6" colspan="1" rowspan="1">

<span class="c2">The job's QOS has reached its time limit.</span>

</td>

</tr>

</tbody>

</table>

<span class="c0"></span>

<span class="c0">Please follow the links for more...</span>

<span class="c0"></span>

<span class="c53">[JOB REASON CODES](https://www.google.com/url?q=https://slurm.schedmd.com/squeue.html%23lbAF&sa=D&ust=1570008089914000)</span>

<span class="c53">[JOB STATE CODES](https://www.google.com/url?q=https://slurm.schedmd.com/squeue.html%23lbAG&sa=D&ust=1570008089914000)</span>

<span class="c0"></span>

## <span class="c43 c44 c40">QoS settings</span>

<span class="c0"></span>

<span class="c43 c40 c30 c7"></span>

<a id="t.001774065333135c85f7249b6b7fd6da4434d52b"></a><a id="t.3"></a>

<table class="c52">

<tbody>

<tr class="c56">

<td class="c49 c68" colspan="1" rowspan="1">

<span class="c43 c40 c30 c39">Command</span>

</td>

<td class="c16 c68" colspan="1" rowspan="1">

<span class="c43 c40 c30 c39">Description</span>

</td>

</tr>

<tr class="c56">

<td class="c49" colspan="1" rowspan="1">

<span class="c40 c30 c55 c7 c57">users</span>

<span class="c34 c7">MaxSubmitJobsPerUser=10</span>

<span class="c34 c7">MaxTRES=cpu=40</span>

<span class="c34 c7">MaxNodes=2</span>

<span class="c34 c7">--account=users</span>

<span class="c77 c51 c55 c7">--qos=short</span>

</td>

<td class="c16" colspan="1" rowspan="1">

<span class="c15 c7">All users</span>

<span class="c7 c15">All partitions</span>

<span class="c43 c77 c51 c7"></span>

</td>

</tr>

<tr class="c56">

<td class="c49" colspan="1" rowspan="1">

<span class="c57 c40 c30 c55 c7">cuda</span>

<span class="c34 c7">MaxSubmitJobsPerUser=10</span>

<span class="c34 c7">MaxTRES=cpu=40</span>

<span class="c34 c7">MaxNodes=2</span>

<span class="c34 c7">--account=cuda</span>

<span class="c7 c34">--qos=cuda</span>

<span class="c34 c7">--gres=gpu:1</span>

</td>

<td class="c16" colspan="1" rowspan="1">

<span class="c15 c7">All users</span>

<span class="c15 c7">Includes cuda partitions</span>

<span class="c15 c7"></span>

</td>

</tr>

</tbody>

</table>

<span class="c0"></span>

<span class="c0"></span>

# <span class="c43 c72 c40">Software</span>

<span class="c2"></span>

## <span class="c43 c44 c40">System software</span>

<span class="c2"></span>

*   <span class="c7">Ubuntu 16.04 LTS</span><span class="c0">  - operating system</span>
*   <span class="c53">[SLURM resource manager](https://www.google.com/url?q=https://slurm.schedmd.com/&sa=D&ust=1570008089922000)</span>

<span class="c2"></span>

### <span class="c43 c44 c40">Compilers and parallel programming libraries</span>

<span class="c2"></span>

*   <span class="c0">GNU Compiler (GCC, GFortran)</span>
*   <span class="c0">Java, Python, Perl, Ruby</span>
*   <span class="c0">OpenMPI - library for MPI message passing for use in parallel programming over Infiniband and Ethernet</span>
*   <span class="c0">...and more. We will be updating this document in future.</span>

### <span class="c43 c44 c40"></span>

### <span class="c43 c44 c40">Libraries</span>

<span class="c2"></span>

*   <span class="c7">Please run the</span> <span class="c40 c7">module avail</span><span class="c0"> command from your ssh console to view a list of available applications.</span>

<span class="c0"></span>

### <span class="c43 c44 c40">Application software</span>

<span class="c2"></span>

*   <span class="c0">Gaussian, Blast, Namd, Gromacs and many more.</span>
*   <span class="c7">Please run the</span> <span class="c40 c7">module avail</span><span class="c0"> command from your ssh console to view a list of available applications.</span>

<span class="c0"></span>

<span class="c0"></span>

# <span class="c43 c40 c54">Contacts and Help</span>

<span class="c2"></span>

<span class="c7">For more information on HPC facilities, systems support, assistance with parallel programming and performance optimisation and to report any problems, contact the CompecTA</span> <span class="c7">Service Desk</span><span class="c0">.</span>

## <span class="c43 c44 c40">Need Additional Help?</span>

<span class="c7">Alternatively you can sent an email to</span> <span class="c53">[support@compecta.com](mailto:support@compecta.com)</span><span class="c0"> this will create a support ticket automatically.</span>

<span class="c0"></span>

<span class="c0">When reporting problems, please give as much information as you can to help us in diagnosis, for example:</span>

<span class="c0"></span>

*   <span class="c43 c40 c62 c7">Your username</span>
*   <span class="c43 c40 c62 c7">Queue/partition name</span>
*   <span class="c43 c40 c62 c7">Job ID(s)</span>
*   <span class="c43 c40 c62 c7">A copy of any error messages</span>
*   <span class="c43 c40 c7 c62">Command used to submit the job(s)</span>
*   <span class="c43 c40 c62 c7">Path(s) to scripts called by the submission command</span>
*   <span class="c43 c40 c62 c7">Path(s) to output files from your jobs</span>
*   <span class="c0">When the problem occurred</span>
*   <span class="c0">What commands or programs you were trying to execute at the time</span>
*   <span class="c7">A pointer to the program you were trying to run or compile</span>

<span class="c0"></span>

<span class="c0"></span>