# Compute Canada 

## Intro

### What is a compute cluster?

![cluster architecture](https://github.com/SMART-Lab/smartdispatch/raw/master/wiki/images/cluster_overview.png)
Image from [SMART Lab](https://github.com/SMART-Lab).

### Getting an account

* Register here: https://ccdb.computecanada.ca/security/login
* Enter your user information. Use Tristan's CCRI: bwf-484-02



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

### Transfer your data

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

### Other topics
* Getting Started Guide: https://docs.computecanada.ca/wiki/Getting_Started_with_the_new_National_Systems
* File systems: https://www.youtube.com/watch?v=66_WGFpjwew


## Clouds

Compute Canada offers an Infrastructure-as-a-Service (IaaS) cloud, that 
is, a way to start Virtual Machines with various base images. This is useful
if you need to host Web services, or if you need a highly-customized software stack that
cannot be deployed easily on a cluster.

### Account creation

 Once you have a Compute Canada account, fill the form 
 [here](https://www.computecanada.ca/research-portal/national-services/compute-canada-cloud/create-a-cloud-account)
 with your CCDB username and email address. This will give you access to one of the Compute Canada clouds:
 * `east.cloud.computecanada.ca`, or
 * `west.cloud.computecanada.ca`

### Starting VMs

* Follow the manual at https://docs-dev.computecanada.ca/wiki/Cloud_Quick_Start
* Don't forget to (1) create a key pair and (2) add port 22 to an Ingress rule if you want to ssh to your VM.
