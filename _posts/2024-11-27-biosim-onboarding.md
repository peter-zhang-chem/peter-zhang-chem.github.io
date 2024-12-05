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
```bash
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

```bash

ssh -i your-key-name your-username@vortex-future.ccr.buffalo.edu -o ServerAliveInterval=60
```
The `-o ServerAliveInterval=60` option sends a keepalive message to the server every 60 seconds, prevent you from disconnected when idel.


I recommend to add the ssh command to your bash resource file `.bashrc` or `.zshrc` if you are on Mac. Nevigate to the file by typing: `vim ~/.bashrc`, add `alias sshccr=ssh -i your-key-name your-username@vortex-future.ccr.buffalo.edu -o ServerAliveInterval=60'`, then activate it by typing `source ~/.bashrc` or restart the terminal. Be sure to not delete or change anything else in your bash resource file.
{: #myid .alert .alert-info .p-3 .mx-2 mb-3}

To get to our group project directory:
```bash
cd /projects/academic/nguyenh
```
To get to our scratch directory:
```bash
cd /vscratch/grp-nguyenh
```

Trajectory Alignment using MD Analysis
-------------
Sometimes, you might need to align a trajectory to a reference frame and save it for analysis. This can come in handy when calculating things like root-mean-sqaure deviation (RMSD) or root-mean-sqaure fluctuation (RMSF). Here, I've shared a script that aligns every frame of an RNA trajectory to its center of mass to make these analyses easier.
```python
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

References:
[Aligning a trajectory to a reference](https://userguide.mdanalysis.org/stable/examples/analysis/alignment_and_rms/aligning_trajectory.html), [On-the-fly transformations](https://userguide.mdanalysis.org/stable/trajectories/transformations.html), [Centering a trajectory in the box](https://userguide.mdanalysis.org/stable/examples/transformations/center_protein_in_box.html#Doing-all-this-on-the-fly)

Alignment to principal axes
-------------
For flexible molecules, it can be useful to align the molecule to its principal axes. I have used this technique to visualize the ion distribution surrounding the flexible single stranded RNA. I do this by utilizing the orient package in VMD, and save the principally aligned trajectory for analysis.

1. Download: [orient](https://www.ks.uiuc.edu/Research/vmd/script_library/scripts/orient/orient.tar.gz) and [la](https://www.ks.uiuc.edu/Research/vmd/script_library/scripts/orient/la101psx.tar.gz). You will need [la](https://www.ks.uiuc.edu/Research/vmd/script_library/scripts/orient/la101psx.tar.gz), the linear algebra package to run orient.

2. unpack the package:

```bash
gunzip orient.tar.gz
tar -xf orient.tar

gunzip la101psx.tar.gz
tar -xf la101psx.tar
```

3. Open VMD and go to VMD TkConsole:

Go to la1.0 folder you got from previous step

```bash
cd la1.0
source la.tcl

```
Go to orient folder you got from previous step

``` bash
cd orient
source orient.tcl
```

4. I provide the script I have to align the principal axes of my RNA to the z-axis of the box

```bash
namespace import Orient::orient
# Get the number of frames in the trajectory
set num_frames [molinfo top get numframes]

# Select all atoms
set sys [atomselect top "all"]

# Set the molecule you are working with, here I select everything that is not Magnesium
set rA [atomselect top "all not name Mg"]

# Iterate over each frame in the trajectory
for {set i 0} {$i < $num_frames} {incr i} {
    # Set the frame
    animate goto $i
    
    # Compute the principal axes and align the molecule
    set I [draw principalaxes $rA]

    # I align the first principal axis to the z axis
    set A [orient $rA [lindex $I 2] {0 0 1}]
    $sys move $A

    # I align the second principal axis to the y axis
    set I [draw principalaxes $rA]
    set A [orient $rA [lindex $I 1] {0 1 0}]
    $sys move $A

    # Update the coordinates for the current frame
    $sys update
    $rA update
}

# Write the modified trajectory to a new file
animate write dcd principal-aligned.dcd

```

References: [Alignment to principal axes in VMD](https://www.ks.uiuc.edu/Research/vmd/script_library/scripts/orient/)

