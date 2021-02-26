## Submitting batch scripts with `sbatch`

Batch job scripts (also known as job scripts) are scripts that contain `#!/bin/bash` at the beginning of each script and are submitted to the slurm workload manager by using `sbatch`. They are scripts that contain code usually written in `bash`. We can use most commands (and a few more) that we would use at the command line within our `sbatch` scripts.

When we submit a script to slurm it is considered a _job_ and gets a unique `job_ID` assigned to it.

First,  to play around with `sbatch` let's create a script called **HelloWorld.sh**.

```shell
mkdir -p ~/trialDirectory
cd ~/trialDirectory
nano HelloWorld.sh
```

At this point, you have made and entered a 'trailDirectory'. The `nano` command will open a command-line text editor. Copy and paste the following in the editor:

```shell
#!/bin/bash

echo Hello World
sleep 1m
date
```

Then exit nano with <kbd>Ctrl+X</kbd>

We can submit this script to **Slurm** with the `sbatch` command.

```shell
sbatch HelloWorld.sh
```

but we receive an error message...

```shell
sbatch: error: Batch job submission failed: Requested time limit is invalid (missing or exceeds some limit)
```

In order to handle jobs, Slurm needs to know the maximum amount of **walltime** your job will run. Walltime can be thought of as the amount of time from the start of your code running to when the last command in your script finishes. We can tell Slurm how much time to allow our submitted script by using the `-t` flag. Let's tell Slurm that our job _shouldn't_ take longer than 5 minutes (note: the format is `dd-hh:mm:ss`).

```shell
sbatch -t 00-00:05:00 -p bmh HelloWorld.sh
```

You will see your job was successfully submitted and will be given an associated Job ID number `Submitted batch job 15219016`

### Flags to use when Submitting Jobs

We can use a number of different flags to specify resources we want from Slurm:

#### `-p` partition flag

The **partition** we would like to use for our job––this will also entail the _priority_ in which our job is submitted (priorities can be high, medium or low). We can request a partition by using the following flag:

 ```shell
 -p <name_of_partition>
 ```

 The farm has the following partitions:
1. parallel nodes names: `high`, `med`, `low`
    - 24 nodes with 64 CPUs and 256GB ram
    - 95 nodes with 32 CPUs and 64GB ram
2. bigmem nodes names: `bmh`, `bmm`, `bml`, `bigmemh`,`bigmemm`, `bigmeml`
    - 13 nodes with 96 CPUs and 1TB ram
    - 9 nodes with 64 CPUs and 512GB
    - 1 node with 96 CPUs and 1024GB

You can find more info on these partitions [here](./jobs_with_slurm/batch_partitions_farm.md).

#### `mem` (memory) flag

the **memory** required to run our job. We can request a specified amount of time with the following flag:

```shell
 --mem=<number>Gb
 ```

 Here `<number>` is the number of Gigabytes of memory required for our job.

 [comment/question]: <> (feel there is type it should be memory instead of time)

#### `mail` flag

we can have slurm **mail** us updates about our job, such as when it starts(`BEGIN`), ends(`END`), if it fails(`FAIL`) or all of the above (`ALL`). There are many other mail-type arguments: REQUEUE, ALL, TIME_LIMIT, TIME_LIMIT_90 (reached 90 percent of time limit), TIME_LIMIT_80 (reached 80 percent of time limit), TIME_LIMIT_50 (reached 50 percent of time limit) and ARRAY_TASKS. We can request slurm emails us with the following flags: 

```shell
--mail-user=<your_email> --mail-type=<argument>
```

#### `-J` Flag (naming Jobs)

We can give jobs specific **names**. To name your job use:

```Shell
-J <job_name>
```

 Be careful, as there is a limit to the number of characters your job name can be.

#### `-o` Flag (output scripts)

Slurm automatically generates **output scripts** where all of the output from commands run from the script are printed to. These will take the form as `slurm-12345.out` where 12345 is an identifying number (the job ID, by default!) slurm assigns to the file. We can change this to any output file name we want. To specify the name of your output file use 

```shell
 -o <file_name>.out
 ```

Slurm can generate **error files**, where all of the errors from the script are printed to. We can ask slurm to create err files and name them with `-e <file_name>.err`

#### `-e` Flag (error)

Slurm can generate **error files**, where all of the errors from the script are printed to. We can ask slurm to create err files and name them with 

```Shell
-e <file_name>.err
```

<br>

If we were hard to ourselves we would write these out at the command line each time we submitted a job to slurm with `sbatch`. It would look something like this:

```Shell
sbatch --time=01-02:03:04 -p bmh --mem=4Gb --mail-user=<your_email> --mail-type=ALL -J <job_name> -o <file_name>.out -e <file_name>.err
```

We would need to switch out all of the `<text>` with parameters specific to our preference, but hopefully you get the gist.

Let's make this easier on ourselves: typing all of the parameters out on the command line every time we want to submit a batch script is annoying and it also doesn't allow us to record what parameters we used easily. We can put the parameters to run each job in the script we submit to slurm! You can refer to the repeatability section to know how to do this.


#### Repeatability

One of the most important things in science is repeatability. However, it is exceptionally easy to run a series of command on data, leave the data for a few months (or years) and come back to the data and have no clue how you went from point A to point Z.

Let's say we lost everything except our backed up raw data and we needed to recreate an analysis. In the worst case, where the commands used to carry out the experiment were not saved, we would have to figure out all of the commands with only a vague memory of the steps we took to get results. It is hard, if not impossible to recreate an analysis with exactly the same string of commands and parameters. So, we should think about documenting things as we go.

In the best case (of this terrible scenario) we would have a script to recreate our analysis! So, we can make this easy for our future forgetful-selves and put all of the flags and commands we submit to Slurm INSIDE our batch scripts!

We can do this by adding **#SBATCH** lines of code after the sh-bang line (`#!/bin/bash`) in our script.

Let's save the parameters we used to run `HelloWorld.sh` within the batch script.

```Console
#!/bin/bash

#SBATCH --mail-user=<email>@ucdavis.edu         # YOUR EMAIL ADDRESS
#SBATCH --mail-type=ALL                         # NOTIFICATIONS OF SLURM JOB STATUS - ALL, NONE, BEGIN, END, FAIL, REQUEUE
#SBATCH -J HelloWorld                           # JOB ID
#SBATCH -e HelloWorld.j%j.err                   # STANDARD ERROR FILE TO WRITE TO
#SBATCH -o HelloWorld.j%j.out                   # STANDARD OUTPUT FILE TO WRITE TO
#SBATCH -c 1                                    # NUMBER OF PROCESSORS PER TASK
#SBATCH --ntasks=1                              # MINIMUM NUMBER OF NODES TO ALLOCATE TO JOB
#SBATCH --mem=1Gb                               # MEMORY POOL TO ALL CORES
#SBATCH --time=00-00:11:00                      # REQUESTED WALL TIME
#SBATCH -p bmh                                  # PARTITION TO SUBMIT TO

echo Hello World
sleep 1m
date
```

Make sure to replace your `<email>` with your UC Davis email address.

Then submit your script:
```
sbatch HelloWorld.sh
```

Once our scripts run, we should see the following files in our current directory: `HelloWorld.j#######.err` and `HelloWorld.j#######.out` these are output (generated from the -o and -e flags) from running a batch job with slurm!

