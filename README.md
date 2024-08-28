# rstudio_server_hpc
Build a singularity container to run rstudio server on a high performance computing (HPC) cluster

# SIF file
Pre-compiled singularity image file can be dowloaded this [link](https://drive.google.com/file/d/15rOVh1zCuR8RmM1Rra1BLvKdqK6Civ2S/view?usp=sharing)

# How to use Rtudio on a HPC
## SSH
Start by login to your HPC cluster by ssh user@domain

```bash
ssh user-id@hpc.domain
# do not run on the head node, you need to have interactive session
interactive -p nocona -c 8
# you need to have singularity software installed on the hpc system

singularity run \
--bind /home/user-id:/mnt/home_hpcc \
--bind /lustre/work/user-id:/mnt/work_hpcc \
./rstudio_centos8.sif /mnt &

# Example of stdout on the screen ----
INFO:    Converting SIF file to temporary sandbox...

RStudio URL:            http://cpu-25-16.localdomain:52673/
RStudio Username:       user-id
RStudio Password:       978c319406e40ad1

You need to open new terminal and ssh user-id@hpc.domain -L 52673:cpu-25-16.localdomain:52673
Then open in new browser localhost:52673

You may need to clean your temporary files by yourself:
RStudio temporary files:        /home/user-id/tmp.vXRaSSze5c

TTY detected. Printing informational message about logging configuration.
Logging configuration loaded from '/etc/rstudio/logging.conf'.
Logging to '/home/user-id/.local/share/rstudio/log/rserver.log'.
# Example of stout on the screen ends ====

# As mention on the stdout you need to open new terminal, ssh with your user id and password
ssh user-id@hpc.domain -L 52673:cpu-25-16.localdomain:52673 # this number will randomly generated according to your node and session

# after you login you need to open new web browser and use RStudio username and password from stdout
New web browser(/docs/web_browser.png)
Succesful login (/docs/rstudio.png)
# Congratulation you run rstudio rserver on an HPC
```
