## TensorFlow
An example job for using TensorFlow and the GPU node of TOSUN cluster could be found in folder `/cta/share/tensorflow`.  

After copying the files to your directory with `cp tensorflow_submit.sh test_single_gpu.py ~` command, an example job can be submitted to the GPU node with 
`sbatch tensorflow_submit.sh` command.  

The output of the job will be saved in `<job_id>-tensorflow.out` file. If you can see the line  
`Single GPU computation time: 0:00:06.992325`
in your output file this means your TensorFlow job is succesfully executed.

An important line in the file `tensorflow_submit.sh`
is `module load tensorflow-gpu-py3-1.15`. This line enables TensorFlow library for your job to use thus should be exist in TensorFlow submission scripts.
You can also create a local environment with pip or conda and install TensorFlow here. 
