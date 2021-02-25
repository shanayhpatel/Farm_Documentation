# Monitoring Jobs

## Monitor Jobs with `squeue`

Oftentimes we submit jobs and would like to know certain things about them -- if they've started, how long they've been running, if they are still running, etc, etc... We can look at the status of any job Slurm is handling by using `squeue`

If we just type

```Shell
squeue
```

we will see **many** rows of jobs....


```
         JOBID PARTITION     NAME     USER ST        TIME  NODES CPU MIN_ME NODELIST(REASON)
      15218450       bmh this_is_ keyu1996 CG       31:10      1 2   100G   bm3
      15219413       bmh     pigz   aminio CG        0:01      1 8   4G     bm2
15108157_[34-4   bigmemm  mapping gfburgue PD        0:00      1 8   200G   (Resources)
14204771_[1182       med freebaye eoziolor PD        0:00      1 4   2000M  (AssocGrpCpuLimit)
15217722_[7-23       bmm     trim hansvgdu PD        0:00      1 2   10G    (JobArrayTaskLimit)
      15113687   bigmemm AA_ophiu jgillung PD        0:00      1 24  200G   (Priority)
      15144078   bigmemm NT_ophiu jgillung PD        0:00      1 24  200G   (Priority)
      15144205   bigmemm AA_plant jgillung PD        0:00      1 24  200G   (Priority)
      15144210   bigmemm NT_plant jgillung PD        0:00      1 24  200G   (Priority)
```

This is a list of **ALL** the jobs currently submitted to Slurm -- which usually quite a few! And often we won't be able to scroll through the list to find our job(s). So, in order to only see your own job(s) we can specify a **username**:

 If you don't know your username, you can find it in a couple of ways: 

1. the `whoami` command:

```Shell
whoami
```

2. with  $USER

```Shell
echo $USER
```

Note: there are subtle differences between the two. The `whoami` command displays the effective user id at the time the command is entered. The `$USER` is an environment variable that is set by the shell--it won't work on all operating systems but it works great here!

We can use the output of this to see the status of the jobs associated with a particular username:

```Shell
squeue -u $USER
```

```Shell
         JOBID PARTITION     NAME     USER ST        TIME  NODES CPU MIN_ME NODELIST(REASON)
      15219530       bmh ggg298-a ggg298-4  R        0:28      1 8   10G  bm14
```

Much better!

Not only can you check on your own job's status but you can also check on the status of your **group**:

```Shell
squeue -A ggg298
```

If you do not know what group you are a part of, you can check!

```Shell
groups
```

```Shell
squeue -A ggg298
```

You can also check on the status of particular partitions:

```Shell
squeue -p bmh
```

These will help you figure out what resources are being used so you can figure out which are free.

