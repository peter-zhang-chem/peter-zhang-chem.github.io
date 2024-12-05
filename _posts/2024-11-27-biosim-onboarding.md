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

>[!TIP]
>
> I recommend to add the ssh command to your bash resource file `.bashrc` or `.zshrc` if you are on Mac. Nevigate to the file by typing: `vim ~/.bashrc`, add `alias sshccr=ssh -i your-key-name your-username@vortex-future.ccr.buffalo.edu -o ServerAliveInterval=60'`, then activate it by typing `source ~/.bashrc` or restart the terminal.


> [!CAUTION]
> 
> Be sure to not delete or change anything else in your bash resource file.
