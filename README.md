# HPC Farm

## Getting Started

- [Farm Access Info](./getting_started/farm_access_info.md) : For prospective investors who want access.

- [Info About Software/Hardware](./getting_started/farmInfo_software_hardware.md) : Info on OS, Software, Hardware( different nodes ) and Batch Partitions on Farm.

- [Login Instructions](./getting_started/login_farm.md) : Info on log in and creating SSH Keys.

[todo]: <> (maybe make a intro in cluster and nodes, node vs cpu goes there)

## Running Jobs with Slurm

- [Job Schedulers and Slurm Introductions](./jobs_with_slurm/slurm_intro.md) : Basics of  Job Schedulers and into to the job scheduler used by Farm i.e. Slurm.

- [Interactive Session on Slurm (`srun`)](./jobs_with_slurm/interactive_session.md) : Information, examples and practices of running an interactive session on slurm with `srun`

- [Submitting Batch Scripts on Slurm (`sbatch`)](./jobs_with_slurm/submitting_scripts.md) : Information, examples and practices of submitting batch scripts on slurm with `sbatch`


- [Monitoring Jobs using `squeue`](./jobs_with_slurm/monitor_jobs.md) : Using `squeue` to monitor jobs and some additional resoueses to monitoring.

[todo]: <> (add link to ganglia)

- [Cancelling Jobs using `scancel`](./jobs_with_slurm/cancel_jobs.md) : Canceling jobs using Job Id, Partition Name or Account.

- Job Queue


## Managing Data on Farm

- [Basics of Space on Farm](./managing_data/space_basics.md) : Checking space that you use, info on how to compress files and tips about managing space.

- [Data Transfer to Farm
](./managing_data/dataTransfer_basics.md) : Info on transferring and uploading data to farm on port 2022 using `screen` and `rsync`.


- [Shared Scratch Space](./managing_data/scratch_space.md) : Info on using the `/scratch/` directory.







