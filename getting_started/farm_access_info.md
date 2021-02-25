# Farm Access

Farm is a research and teaching cluster for the College of Agricultural and Environmental Sciences. This page will go over accessing the Farm cluster.

## Access Policy

All researchers in College of Agriculture and Environmental Sciences are entitled to free access to the original 8 nodes with 24 CPUs each and 64GB ram in the low, med, and high partitions.

[comment]: <> (Confused on partition and what to link if users want to know more about partitions.)
[todo]: <> (Add link to info on different partitions)

Any new nodes purchased will be in the “Farm III” pool separate from existing farm partitions. Currently (June 2019) the “Farm III” pool has 24 “parallel” nodes and 13 “bigmem” nodes.

<details>

  <summary> Costs to add to farm III (open) </summary>

- $ 8,800 for a “parallel” node with 256GB ram and 64 CPUs (in the low2, med2, and high2 partitions)
- $22,700 for a “bigmem” node with 1TB of ram and 96 CPUs (in the bmh, bmm, and bml partitions)
- $ 1,000 for 10TB of storage, this does NOT include backups
- $17,500 for a GPU node (dual socket Xeon 4114 + Nvidia V100)

Everyone gets free access to a common storage pool for 1TB per user. If you need more please email help@cse.ucdavis.edu. Unless special arrangements are made there are no backups. Please plan accordingly.

Researchers with bigger storage needs can purchase storage at a rate of $1,000 per 10TB.
</details>

<br>

For access to the cluster, please fill out the [Account Request Form](http://wiki.cse.ucdavis.edu/cgi-bin/index2.pl). Choose “Farm” for the cluster, and if your PI already has access to Farm, select their name from the dropdown. Otherwise, select “Getchell” as your sponsor and notify [Adam Getchell](mailto:acgetchell@ucdavis.edu). Please review the Getting Started section.

[todo]: <> (make getting started section and link it, add log in and ssh key instructions)

Purchases can be split among different groups, but have to accumulate until a full node is purchased. Use of resources can be partitioned according to financial contribution.

[todo]: <> (feel Monitoring should be somewhere else)

## Monitoring

Ganglia is available at [http://stats.cse.ucdavis.edu/ganglia/?c=Agri&m=load_one&r=hour&s=descending&hc=4&mc=2]

[todo]: <> (some context about ganglia and what is does, make link look better)

## Additional information for prospective investors

You will be notified when your hardware has been installed and your account has been updated. Rather than giving you unlimited access to the specific hardware purchased, the account update will give you high-priority access to a “fair share” of resources equivalent to the purchase. For example, if you have purchased one compute node, you will always have hi-priority access to one compute node. There is no need to worry about the details of which node you are using or which machine is storing your results. Those details are handled by the system administrators and managed directly by slurm.

Slurm is configured you get 100% of the resources you paid for within 1 minute in the high partition. Access to unused resources is available though the medium and low partitions. Users get a “fair share” of free resources. So if you contribute twice as much as another user you get twice as large a share of any free resources.