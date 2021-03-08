
## Batch Partitions

**Farm is shared by users**. There is a queue established with multiple users submitting jobs. This means often times [Slurm](../jobs_with_slurm/slurm_intro.md) will allocate resources to your jobs only when nodes in your desired partition are open and not occupied by jobs from other users. In order to submit a job (covered [here](../jobs_with_slurm/slurm_intro.md)), you must specify which partition your job(s) will run on. Based on your memory and cpu requirements, and resources bought by you, you can choose to run with the following partition options:

### Basic Types of Partitions

**Low** priority means that you might be killed at any time. Great for soaking up unused cycles with short jobs; a particularly good fit for large array jobs with short run times.

**Medium** priority means you might be suspended, but will resume when a high priority job finishes. **NOT** recommended for MPI jobs. Up to 100% of idle resources can be used.

**High** priority means that your job will kill/suspend lower priority jobs. High priority means your jobs will keep the allocated hardware until it's done or there's a system or power failure. Limited to the number of CPUs your group contributed. Recommended for MPI jobs.

[todo]: <> (little repetitive but am confused on how to change)

## Partitions in Farm and their priority

- **bigmeml** (low): This means that your job might be killed at any time (but then restarted). Great for soaking up unused cycles with short jobs; a particularly good fit for large array jobs with short run times.

- **bigmemm** (medium): This means your jobs might be suspended, but will resume when a high priority job finishes. Good for long jobs that need lots of cpu, but NOT recommended for MPI jobs. Up to 100% of idle resources can be used.

- **bigmemh** (high) or (h): Your job will kill/suspend lower priority jobs. High priority means your jobs will keep the allocated hardware until it's done or there's a system or power failure. Limited to the number of CPUs your group contributed. Please check with your supervisor or others before running anything using more than 16 cpu on bigmemh, as we only have 128 slots on this queue.


- **med**: These are the older parallel nodes. For many jobs not needing high memory, the parallel queue is still the way to go. There are many hundreds of cpu there, but we only have access to them at medium priority. Note that each node in this queue only has 24 cpu and 32G of RAM, so plan your scripts accordingly.

- **high2**: These are the nodes Jeff paid for. Users in Jeff's group can use up to 512GB ram and 128 CPUs.

- **med2**: "fair" share of idle nodes, might be suspended. Priority = 20, which let you get 2/8th of idle nodes if it's contended, and up to 100% of the 8 nodes if not.

- **low2**: "fair" share of idle nodes, might be killed and rescheduled. Priority = 20, which let you get 2/8th of idle nodes if it's contended, and up to 100% of the 8 nodes if not.

Farm II's bigmem partitions are named **bml**, **bmm**, and **bmh**.

To use these, we specify the partition in either `sbatch` or our batch script itself.

To do so with `sbatch`, do:

```Shell
$sbatch -p bigmemh steve.sh 
```

Or, we can do so in the batch script itself by adding a line:

```Shell
#SBATCH --partition=bigmemh
```

You can also submit jobs to a specific node in bigmem (say bigmem9) by including -p bigmemh --nodelist=bigmem9 in your sbatch command line.

