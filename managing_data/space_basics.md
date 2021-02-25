
## Basics of Space on Farm

Each group only has so much space on the cluster. Memory can be bought but it is good practice to always compress and delete files as you run analyses. That way, there won't be an extra terabyte of unnecessary sequence data files hanging around.

To check the amount of space you have left as a group use:

```Shell
df -h | grep <username>
```

It is also useful to know how much space you are taking up:

```Shell
du -d 0 -h
```

As in all computational steps, there are a number of different ways to go about compressing files.

- `gzip`
  - pros: fastest compression & decompression, small memory footprint
  - cons: compressed files are not as small
- `bz2`
  - pros: middle sized compression ratio
  - cons: slower than both gzip and lzma
- `lzma`
  - pros: smallest compressed files, decompression speed similar to gzip
  - cons: memory intensive to compress, not found on all systems (but on the farm!)

#### Tips and Practices for Managing Space

Good cluster practice involves realizing that many things on the cluster are shared, that includes storage. Currently, there is ~80 Tb of space. That sounds like a lot, but after data and outputs are generated from the many jobs you are bound to run, the cluster will begin to feel a little too clustered. (As an example, fastq files from 8 maize individuals sequenced to 30X will already be close to 1Tb of space if not compressed).

Use `du -sh` to check the amount of storage being used in any given directory. Just cd to the directory of your choice and enter that command and options. **Check directory size regularly**. Please limit your home directory (`~/`, which equals `/home/yourusernamehere/`) to 1 Tb of disk space.

Use `df -h `to check the size of your drive, its total storage being used, how much you have left on your drive, and where that drive is mounted.

[todo]: <> (what if user needs more space? the rilab docs tells users to check additional directories and then inform the slack channel)