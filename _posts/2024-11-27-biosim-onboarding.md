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
![image](assets/key-gen-example.png)

At the end, in the `~/.ssh` directory, you should find the public key and the private key. In my case, I have `testing.pub` as my public key and `testing` as my private key Copy the content of the public key to the [CCR](https://idm.ccr.buffalo.edu/sshkey). Wait for approval and you can login to CCR using ssh. You should do this process for every machine that you wish to connect to CCR from.

Here is an example of my CCR account, I have three machine registered:
![image](assets/CCR-keys.png)

References:
[Generate New SSH Key](https://docs.ccr.buffalo.edu/en/latest/hpc/login/#generate-new-ssh-key)

