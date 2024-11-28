---
title: Generate public and private key for UB CCR Login
author: Peter Zhang
date: 2024-11-27
category: Jekyll
layout: post
mermaid: true
---

To use the secure shell (SSH) to connect to CCR's login servers, you will need to generate a new SSH key on your local machine.

Go to your '.ssh' directory on your machine by typing in 'cd .ssh'.

```
ssh-keygen -t ed25519 -C "email@buffalo.edu"
{: .block-tip }

The -t option here specify which type of secure key to generate. Ed25519 refers to speicifc elliptic curve algorithm that you can read more about [here] (https://ed25519.cr.yp.to/). The -C option expects you to add an comment to the key, here you should put your Buffalo email address.

Here is an example:

```
> (base) pz@Peters-MacBook-Pro-9 ~ % ssh-keygen -t ed25519 -C hzhang79@buffalo.edu
> Generating public/private ed25519 key pair.
> Enter file in which to save the key (/Users/pz/.ssh/id_ed25519): "ANY_NAME"
> Enter passphrase (empty for no passphrase)
> Your public key has been saved in "ANY_NAME".pub
>The key fingerprint is:
SHA256:sycoqrxsIOLqiexYPnHTVldIN/nV4KDJ6rpJem1XPmk hzhang79@buffalo.edu
The key's randomart image is:
+--[ED25519 256]--+
|         ...+....|
|         ..+o+  o|
|          +. ... |
|        ...   .  |
|     . .S.       |
|+ . o oo o  .    |
|= .o.oo.+ .o .   |
|*=o. +.ooo. E    |
|XX+...+o . . .   |
+----[SHA256]-----+
{: .block-tip }

In the same directory, you should have a private key with "ANY_NAME", and a public key with "ANY_NAME.pub". Copy the content of the public key to the [CCR] (https://idm.ccr.buffalo.edu/sshkey). Wait for approval and you can login to CCR using ssh. You should do this process for every machine that you wish to connect to CCR from.