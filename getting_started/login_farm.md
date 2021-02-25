# Connecting to Farm

## Quick Intro to using Farm

Farm has a **head node**, which controls the cluster and **compute
nodes** which is where the action happens. Farm runs on a cluster workload management system called
[Slurm](https://slurm.schedmd.com). For the most part, you
interact with Farm using scripts to launch jobs on the compute nodes;
you don't run processes on the head node and you don't log into the
compute nodes directly. The only tasks that acceptable on the head node are:

[todo]: <> (add a picture for better understanding)

- Downloading files (with `wget` or `curl`)
- Compiling/building files
- Installing R packages
- Submitting or checking on jobs

## Connecting with Farm

The address is `username@agri.cse.ucdavis.edu`. `username` here will
be your UCD kerberos ID. You will have to have generated a SSH key
and given the **public** key part (do not share the private key!) to
CSE Help.

If you don't already have access to Farm, you can know more about on the  [Farm Access Page](./farm_access_info)

[comment/question]: <> (It is not CSE help right now, what is it?)
[comment/todo]: <> (check if this link works on github as well)

## Creating an SSH Key and Farm Account


In order to create an account on Farm you need to have an SSH public key. This key is a file created on your local computer (not Farm) that allows you to authenticate with
Farm.

[comment/question]: <> (is the process same for windows/unix?)
[comment/question]: <> (maybe add that the passphrase can't be seen and is imp or something)

1. Generate your key with `ssh-keygen`. Be sure to use a passphrase.

        $ ssh-keygen -b 2048
        Generating public/private rsa key pair.
        Enter file in which to save the key (/Users/username/.ssh/id_rsa):
        Enter passphrase (empty for no passphrase):
        Enter same passphrase again:
        Your identification has been saved in /Users/username/.ssh/id_rsa.
        Your public key has been saved in /Users/username/.ssh/id_rsa.pub.
        The key fingerprint is:
        e1:1e:3d:01:e1:a3:ed:2b:6b:fe:c1:8e:73:7f:1f:f0 
        The key's randomart image is:
        +--[ RSA 2048]----+
        |.o... ...        |
        |  .  .   o       |
        | .     *         |
        |  .  o +         |
        | .   S .         |
        |  o   E          |
        |   +     .       |
        |oo+..  . .       |
        |+=oo... o.       |
        +-----------------+

**WARNING:** There are two keys generated: private and public. The
  public key is sent to the Farm (or any other servers you have access
  to) and the private key stays where it is. **Never share or transfer
  your private key -- keep it safe and private.** Any computer with
  your private key can log in to your account. Treat your private key
  like a password.

2. Your keys are located in the `~/.ssh/` directory:

        /Users/[username]/.ssh

[comment/question]: <> (might be different if the user chooses a different folder?)

Your public key is in a file called `id_rsa.pub`. 

3. Attach `id_rsa.pub` to the [application form](http://wiki.cse.ucdavis.edu/cgi-bin/index2.pl) for an account. Make sure to ask to be part of the Ross-Ibarra group. Note that the admins and Jeff have access to log into your account if needed; signing up for an account on the cluster constitutes permission to allow this access.

[comment/question]: <> (who is jeff annd this info  might not be relevant/change)

## SSH Config

Make your life a little easier by adding the following to `~/.ssh/config`:

    Host farm
        HostName agri.cse.ucdavis.edu
        User username

Replace `username` with your username. This will allow you to ssh to
farm with just `ssh farm` in the future.