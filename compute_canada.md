# Compute Canada 

## Intro

### What's a compute cluster?

[[https://github.com/SMART-Lab/smartdispatch/blob/master/wiki/images/cluster_overview.png|alt=Cluster Overview]]
Image from [SMART Lab](https://github.com/SMART-Lab).

### Getting an account

* Register here: https://ccdb.computecanada.ca/security/login
* Enter your user information. Use Tristan's CCRI: bwf-484-02

 To access the cloud, you will also have to fill in the form 
 [here](https://www.computecanada.ca/research-portal/national-services/compute-canada-cloud/create-a-cloud-account)
 with your CCDB username and email address.

### Where to get help?

* Email support: ```support@computecanada.ca```
* Wiki: [https://docs.computecanada.ca/wiki/Compute_Canada_Documentation](https://docs.computecanada.ca/wiki/Compute_Canada_Documentation)

## Clusters

### Available clusters

General-purpose:
* [Cedar](https://docs.computecanada.ca/wiki/Cedar)
* [Graham](https://docs.computecanada.ca/wiki/Graham) 

Specialized for parallel jobs:
* [Niagara](https://docs.computecanada.ca/wiki/Niagara)

### Connect to a cluster

Pick one general-purpose clusters:
* ```graham.computecanada.ca```
* ```cedar.computecanada.ca```

Connect using ssh:
```ssh <username>@graham.computecanada.ca```

You are now connected to a login node, as the prompt shows:

```[<username>@gra-login1 ~]$```

 This is a shared computer, which must be used only for lightweight 
 operations such as file transfers, job submissions, etc Data 
 processing or compilation must be done on /compute nodes/.

### Access a compute node, interactively

```salloc --time=1:0:0 --ntasks=1 --account=def-glatard```

The prompt will tell you the name of the computer that was allocated to you [here, ```gra796```]:

```[<username>@gra796 ~]$```


### Access a compute node, in batch mode

Create a script:

```echo '#!/bin/bash' > script.sh ; echo echo Hello >> script.sh```

Make it executable:

```chmod 7555 ./script.sh```

Submit it!

```sbatch --time=00:30:00 script.sh```

Monitor your job(s):

```squeue -u <username>```

Your job will write its output in your home folder:

```
$ cat slurm-4811758.out 
Hello
```

### Transferring your data

The easiest way to transfer your files to/from clusters is through ```scp```, 
a copy command that works over ```ssh```:

```scp file.txt <username>@graham.computecanada.ca:.```

### Use pre-install software

The ```module``` command shows the software packages that are already installed on the cluster and ready to use:

```module avail```

If you want to use a specific software package, say ```vtk```, just type:

```module load vtk```


### Install your code

You might want to install your own code on the cluster. Here are a few options:

* Source code: Git clone your repository from GitHub on the cluster.
* Python code: create a 
[virtualenv](https://www.dabapps.com/blog/introduction-to-pip-and-virtualenv-python)
and install all the dependencies in it with ```pip```.
* Linux binaries: copy them directly to the cluster.
* C/C++: if your code needs to be recompiled, submit an interactive job and compile your code there.
* Install your code in a Singularity container and run it on the cluster (```module load singularity```).


## Clouds

### What's a cloud?

https://docs-dev.computecanada.ca/wiki/Cloud_Quick_Start

https://www.computecanada.ca/research-portal/national-services/compute-canada-cloud/create-a-cloud-account/

