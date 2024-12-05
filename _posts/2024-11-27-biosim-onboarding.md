---
title: Biosim lab tips
author: Peter Zhang
date: 2024-11-27
category: Jekyll
layout: post
---
Generate ssh key for UB CCR
-------------

To use the secure shell (SSH) to connect to CCR's login servers, you will need to generate a new SSH key on your local machin:
```
ssh-keygen -t ed25519 -C "email@buffalo.edu"
```
The `-t` option specifies which type of secure key to generate. `Ed25519` refers to speicifc elliptic curve algorithm that you can read more about [here](https://ed25519.cr.yp.to/). The `-C` option expects you to add an comment to the key, here you should put your Buffalo email address.

Here is an example:
![image](/assets/keygen.png)

At the end, in the `~/.ssh` directory, you should find the public key and the private key. In my case, I have `testing.pub` as my public key and `testing` as my private key Copy the content of the public key to the [CCR](https://idm.ccr.buffalo.edu/sshkey). Wait for approval and you can login to CCR using ssh. You should do this process for every machine that you wish to connect to CCR from.

Here is an example of my CCR account, I have three machine registered:
![image](/assets/ccrkey.png)

References:
[Generate New SSH Key](https://docs.ccr.buffalo.edu/en/latest/hpc/login/#generate-new-ssh-key)

Login to UB CCR and nevigate to our group folder
-------------
Now you have uploaded your public key to CCR and your matching private key in the `.ssh` folder, you can fire up a terminal window and log onto CCR!

```

ssh -i your-key-name your-username@vortex-future.ccr.buffalo.edu -o ServerAliveInterval=60
```
The `-o ServerAliveInterval=60` option sends a keepalive message to the server every 60 seconds, prevent you from disconnected when idel.


I recommend to add the ssh command to your bash resource file `.bashrc` or `.zshrc` if you are on Mac. Nevigate to the file by typing: `vim ~/.bashrc`, add `alias sshccr=ssh -i your-key-name your-username@vortex-future.ccr.buffalo.edu -o ServerAliveInterval=60'`, then activate it by typing `source ~/.bashrc` or restart the terminal. Be sure to not delete or change anything else in your bash resource file.
{: #myid .alert .alert-info .p-3 .mx-2 mb-3}

To get to our group project directory:
```
cd /projects/academic/nguyenh
```
To get to our scratch directory:
```
cd /vscratch/grp-nguyenh
```

Trajectory Alignment using MD Analysis
-------------
There will be times you want to align a trajectory to a reference frame and write it to a file for analysis. This can be useful when calculating values such as root-mean-sqaure-deviation(RMSD), or root-mean-sqaure-fluctuation (RMSF). Here I provide a script to align every frame of a trajectory containing RNA to its center of mass.
```
import os
import numpy as np
import MDAnalysis as mda
from MDAnalysis import transformations as trans
from MDAnalysis.analysis import align

def align_COM(directory, pdb, dcd)
    os.chdir(directory)
    
    # Create an Universe with the trajectory(dcd) and topology file(pdb)
    u = mda.Universe(pdb, dcd)
    
    # Define your box size (here all edge is 720 angstrom with 90 degree angles)
    dim = np.array([720, 720, 720, 90, 90, 90])
    
    # Select the molecule you want to align (I am working with RNA, so Adenine in my case, you can print out your selection to see if you are selecting your intended molecule)
    ADE = u.select_atoms('resname ADE')

    # Define your workflow, here I set my box dimension, unwrap all atoms, center ADE's (I defined earlier) center of mass to the center of box, then I wrap all the atoms.
    workflow = [trans.boxdimensions.set_dimensions(dim),
                trans.unwrap(u.atoms),
                trans.center_in_box(ADE, center='mass'),
                trans.wrap(u.atoms)]
    
    # use add_transformations to apply the workflow you defined earlier to the trajectory
    u.trajectory.add_transformations(*workflow)

    # now your trajectory is aligned, to save it I use the align.AlignTraj function. Here I save my new trajectory as "md-align-wrap.dcd" 
    align.AlignTraj(u, u, select='resname ADE', filename="md-align-wrap.dcd", match_atoms=True).run()
```
