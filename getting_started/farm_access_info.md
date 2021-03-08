# Farm Access

Farm is a research and teaching cluster for the College of Agricultural and Environmental Sciences. This page will go over accessing the Farm cluster.

## Access Policy

All researchers in CA&ES are entitled to free access to 8 nodes with 24 CPUs and 64GB RAM each (up to a maximum of 192 CPUs and 512GB RAM) in Farm II’s low, medium, and high priority batch queues, as well as 1TB storage space.

Additional usage and access may be purchased by contributing to Farm III by through the node and/or storage rates, or by purchasing equipment and contributing through the rack fee rate.

Contributors always receive priority access to the resources that they have purchased within one minute with the “one-minute guarantee.” Users can also request additional unused resources on a “fair share” basis–someone who contributes twice as much will be able to use twice as many unused resources in the medium or low partitions.

[comment]: <> (Confused on partition and what to link if users want to know more about partitions.)
[todo]: <> (Add link to info on different partitions)

## Current Rates

Updated info on current rates and latest farm hardware specifications can be found at HPC Website : [https://hpc.ucdavis.edu/farm-cluster]() 

<!-- <details>

  <summary> Costs to add to farm III (open) </summary>

- $ 8,800 for a “parallel” node with 256GB ram and 64 CPUs (in the low2, med2, and high2 partitions)
- $22,700 for a “bigmem” node with 1TB of ram and 96 CPUs (in the bmh, bmm, and bml partitions)
- $ 1,000 for 10TB of storage, this does NOT include backups
- $17,500 for a GPU node (dual socket Xeon 4114 + Nvidia V100)

Everyone gets free access to a common storage pool for 1TB per user. If you need more please email help@cse.ucdavis.edu. Unless special arrangements are made there are no backups. Please plan accordingly.

Researchers with bigger storage needs can purchase storage at a rate of $1,000 per 10TB.
</details>

<br> -->

## Get your account on Farm

For access to the cluster, please fill out the [Account Request Form](http://wiki.cse.ucdavis.edu/cgi-bin/index2.pl). Choose “Farm” for the cluster, and if your PI already has access to Farm, select their name from the dropdown. Otherwise, select “Getchell” as your sponsor and notify [Adam Getchell](mailto:acgetchell@ucdavis.edu). Please review the Getting Started section.

[todo]: <> (make getting started section and link it, add log in and ssh key instructions)

Purchases can be split among different groups, but have to accumulate until a full node is purchased. Use of resources can be partitioned according to financial contribution.

## Additional information for prospective investors

You will be notified when your hardware has been installed and your account has been updated. Rather than giving you unlimited access to the specific hardware purchased, the account update will give you high-priority access to a “fair share” of resources equivalent to the purchase. For example, if you have purchased one compute node, you will always have hi-priority access to one compute node. There is no need to worry about the details of which node you are using or which machine is storing your results. Those details are handled by the system administrators and managed directly by slurm.

Slurm is configured you get 100% of the resources you paid for within 1 minute in the high partition. Access to unused resources is available though the medium and low partitions. Users get a “fair share” of free resources. So if you contribute twice as much as another user you get twice as large a share of any free resources.