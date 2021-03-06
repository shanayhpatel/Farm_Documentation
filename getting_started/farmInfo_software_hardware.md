# Technical Specifications

## Operating System

**Farm II** cluster runs Ubuntu 18.04. Farm II uses the [slurm batch queue manager](./jobs_with_slurm/slurm_intro.md). System configuration and management is via cobbler and puppet.

[todo]: <> (Cobbler and puppet, any docs for cobbler and puppet?)

## Software

Requests for any centrally installed software should go to [farm-hpc@ucdavis.edu](mailto:farm-hpc@ucdavis.edu ) . Any software that is available in CentOS/Ubuntu is also available for installation or already installed on this cluster. In many cases we compile and install our own software packages. These custom packages include compilers, mpi layers, open source packages, commercial packages, HDF, NetCDF, WRF, and others. We use Environment Modules to manage the environment. A quick intro:

- To get a list of available applications and libraries `module avail`
- To setup your command line or script based environment - `module load <directory/application>`

Documentation on some of the custom installed software is at [HPC Software Documentation](https://wiki.cse.ucdavis.edu/support:hpc). An (outdated) list is at [Custom Software](https://wiki.cse.ucdavis.edu/support:hpc:software). Best to use the “module avail” command for the current list of installed software.

[todo]: <> (New link once software packages documentation is ready, talk about what we want to keep)

## Hardware

Hardware specifications of Farm.

Hardware from both Farm II and Farm III are still in service; Farm I has been decommissioned as of 2014.

**Interconnect**

- Farm III: 2 x 36 port 100Gbps Infiniband switches
- Farm II: Three 36 port QDR (40Gbps) Infiniband switches
- Farm I: Collection of 1Gbitx48 switches

**Large Memory Nodes on Farm** (bigmen partition)

- Farm III - 13 1TB Bigmem nodes with 96 CPUs
- Farm II - 9 512GB Bigmem nodes with 64 CPUs and 1 1024GB node with 96 CPUs.

**Farm II Interactive head node**

- Farm, 12 cores/24 threads total, Intel Xeon E5-2620, 64 GB RAM (Samsung M393B1K70DH0-CK0 8x8GiB), 1x1TB Seagate ST1000NM0011 drive

**File Servers on Farm II**

- **NAS-8-0**, 9x11TB = 100TB Usable
- **NAS-8-1**, 3x 7TB = 21TB
- **NAS-8-2**, 3x11T and 2*17B = 67TB
- **NAS-8-3**, 4x11TB = 44TB
- **NAS-9-0**, 6×8.2TB = 50TB
- **NAS-9-1**, 6×8.2TB = 50TB
- **NAS-9-2**, collection = 30TB
- **NAS-10-1**, 22T * 9 = 200TB
- **NAS-10-3**, collection = 50TB
- **NAS-10-4**, collection = 131TB
- **NAS-11-0**, 9x28TB = 252TB
- **NAS-11-1**, 9x22TB = 200TB
- **NAS-11-2**, 9x22TB = 200TB
- **NAS-12-1**, 9x28TB = 252TB
- **NAS-12-2**, 4*87TB = 350TB
- **NAS-12-3**, 4*87TB = 350TB

Farm also has multiple other file servers with over 5.3PB of storage space total.



[todo/question]: <> (ask for other files servers for updated info)

**Infiniband interconnect currently on Farm II (32Gbps)** (high, low, and medium queue)

- 2 48-port HP 1810-48G switches
- 1 KVM console
- 2 APC racks
- 4 managed PDUs

(This info was last updated March 2021)
