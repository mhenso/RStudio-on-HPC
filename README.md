# rstudio_server_hpc
Build a singularity container to run rstudio server on a high performance computing (HPC) cluster

# SIF file
Pre-compiled singularity image file can be dowloaded this [link](https://drive.google.com/file/d/15rOVh1zCuR8RmM1Rra1BLvKdqK6Civ2S/view?usp=sharing)

# How to use Rtudio on a HPC
## SSH
Start by login to your HPC cluster by ssh user@domain

```bash
ssh hpc.user@hpc.domain
# do not run on the head node, you need to have interactive session
interactive -p nocona -c 8



```
