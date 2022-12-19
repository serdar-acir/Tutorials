[![Documentation Status](https://readthedocs.org/projects/su-hpc-tutorials/badge/?version=latest)](https://su-hpc-tutorials.readthedocs.io/en/latest/?badge=latest)
      

# Sabancı HPC Tutorials

## Getting into Tosun Cluster

### Within campus
`ssh username@tosun`

### From outside of campus
`ssh username@flow.sabanciuniv.edu`  
Then  
`ssh username@tosun`  

## Saving Your Output
While submitting your job to query, there are several ways to save your output.  
  
- Output could be directed to a file by command   
    - `./some_task > out.txt` will *write* your output to the file **out.txt**  
    - `./some_task >> out.txt` will *append* your output to the file **out.txt**  
    - `./some_task &>> out.txt` will *append* your output *and* stderror to the file **out.txt**  


## Redirecting Output
This output later could both be viewed and edited or copied to local.  
  
- To view output; `cat` command could be used or editing file nano editor could be used with `nano out.txt` command.  
- To copy the output to your local computer; 
    - From local `scp username@tosun:/absolute/path/to/file /relative/path/in/local`
    - From cluster `scp /relative/path/in/local username@local:/absolute/path/to/directory` could be used.    
