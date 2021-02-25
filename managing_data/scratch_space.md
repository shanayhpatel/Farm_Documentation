## Shared scratch space

Each node has a `/scratch/` directory, which you can use to write intermediate files. But as this is space shared across all Farm users, you need to remove files when you are finished. Usually, you can do this with `rm` within your submission script, but sometimes files can be left behind, like if your script encounters errors before erasing the file.

If this happens in an array job, you might not know which nodes to clean up. First, find all nodes that might be affected with `sinfo`, then loop through the nodelist to ssh and remove files ``` for i in `scontrol show hostname c8-[62-64,67-77,87-89,91-96] `; do echo $i; ssh $i rm -rf /scratch/mstitzer/*;done ```

In addition, we have a group scratch directory `/group/jriscratch`. They are raid0 so no protection or backup. The idea is to use those as a scratch drive when running something super I/O intensive. Should be many times faster than writing to local scratch. Please note it’s only 2Tb for whole lab so you can NOT store anything there. Just for scratch purposes. Probably a good idea to mention in #farm_issue channel on slack if you plan to use it so it doesn’t fill up.