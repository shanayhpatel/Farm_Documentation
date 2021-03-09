# Intro to Job Schedulers and Slurm

## Job Schedulers

In order to carry out commands that are memory intensive we need to use auxiliary computers that will not affect the login/head node. **NOTE:** sometimes merely copying large files is memory intensive enough that we will need to use computers other than the head node! To request resources to run our scripts we use _job schedulers_. Job schedulers handle how to allocate the compute cluster's resources to batch job scripts submitted by users.

There are a number of different flavors of job schedulers. The job scheduler you will be submitting jobs to is specific to the cluster you are using at your institution but they all have the following general structure:

![Job Scheduler Working Image](https://i.imgur.com/9rSbIxR.png)

The job scheduler evaluates when resources will be dedicated to a job based on the:

- partition & priority (`-p`)
- how much of  the group's resources are already being used
- requested wall time (`-t`)
- requested resources
  - memory (`--mem`)
  - CPUs (`-c`)

## Slurm Intro

[Slurm](https://slurm.schedmd.com/documentation.html) is an open source workload manager that is commonly used on compute clusters (both the Farm and Barbera use Slurm). It handles allocating resources requested by batch scripts.

There are **two** main ways you can request resources using Slurm:

1. Running an interactive session with `srun`([Learn more](./interactive_session))
2. Submitting batch script with `sbatch`([Learn more](./submitting_scripts))

For all basic commands : [Slurm Commands Cheat Sheet](https://slurm.schedmd.com/pdfs/summary.pdf)

If you are familiar with some other workload manager( PBS/Torque, Slurm, LSF, SGE or LoadLeveler ), a cheat sheet comparing the commands can be found  [here](https://slurm.schedmd.com/rosetta.html).
