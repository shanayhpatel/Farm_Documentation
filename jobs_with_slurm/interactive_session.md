## Interactive Sessions

`srun` command is used to start an interactive session.

Interactive sessions allow you to work on computers that aren't the login/head node. Essentially you can use the computer clusters to interactively through the command line interface. This is really powerful for doing memory intensive commands that you may not need to keep track of. However, with this power comes a great danger.

[comment/question]: <> (something about jetstream in official doc, little context needed to make sure I have the right info)

**Useful tips to keep in mind while using `srun`**

- The commands you run will not be saved in scripts anywhere. So, if you wanted to go back and recreate an analysis, you won't know what you've run, how you've run it or which versions of software you used.

To request and launch a basic interactive session that will last for two hours use the following:

```Shell
srun --time=02:00:00 --pty /bin/bash
```

Pay close attention to the time you give to yourself using `srun`! Slurm will terminate the session immediately at the end of the allotted time. It, sadly, doesn't care if you are 99.99% of the way through your analysis

Also, you can request more/different resources by using to following flags:

- `--mem=<number>` = request a certain amount of memory, default is Megabytes ( 1Gb = 1024 Mb)

- `-c <number>` = request a certain number of CPUs

- `--pty R` = request an interactive R session

- `-p <partition_name>` = srun on the the specified partition 

### Example of using bigmemh  to work interactivity with R with 16 gigabytes memory

```Shell
$ssh -X farm
$srun -p bigmemh -t 2:00:00 --mem 16384 --pty R
```

If you want to render R plots to your local computer through X11, here is a solution:

```Shell
$srunx your-partition
```

Make sure your `X11` is open before you typing the command.

Using `ssh -Y` with `X11` may seem like good idea, but this does not specify a partition to work interactively in, so you will end up running things on the head node. **This is not ideal**.

A **very important** bit of advice: remember to save and close your R sessions, as a network interruption will lead to a loss of your connection and data. Be sure to maintain your work in a script locally too. Also, when you're done, always close your R session. If not, SLURM will assume you are still using the session and its resources will held from other users.
