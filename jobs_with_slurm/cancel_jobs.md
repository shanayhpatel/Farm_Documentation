## Cancel your jobs with `scancel`

To cancel a single job you can specify the `JOBID`

```Shell
scancel <job_ID>
```

To cancel all of the jobs that belong to you, use the `-u`flag.

```Shell
scancel -u <username>
```

There are any number of ways to cancel jobs. You can by job name with `-n`, partition name `-p`, account `-A` and can use regular expressions to cancel a list of jobs. BUT be careful how you cancel!