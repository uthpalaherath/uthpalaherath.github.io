---
title: Advanced resource monitoring on HPC clusters
excerpt: 
date: 2025-02-05
toc: true
tags:
  - hpc
  - bash
  - linux
header:
  teaser: /assets/media/2025-02-05-Advanced-resource-monitoring-on-HPC-clusters/2025-02-05-Advanced-resource-monitoring-on-HPC-clusters-20250206132157590.png
---
{: .notice--primary}
*In this post, I share a script that utilizes seff, sstat, and sacct for advanced resource monitoring on HPC clusters.*

![2025-02-05-Advanced-resource-monitoring-on-HPC-clusters-20250206132157590](/assets/media/2025-02-05-Advanced-resource-monitoring-on-HPC-clusters/2025-02-05-Advanced-resource-monitoring-on-HPC-clusters-20250206132157590.png)

Happy 2025, everyone! Although it might feel a little late for New Year’s greetings, this is my first post of the year, so I hope you all have a wonderful 2025.

This semester, as a volunteer instructor for the course ME511 (Computational Materials Science)[^3] at Duke University, I had the opportunity to access Duke's Research Computing Cluster, DCC[^1],  to setup and test the Density Functional Theory (DFT) code, FHI-aims[^2] for electronic structure calculations and molecular dynamics simulations. Learning through examples and exercises using this code, students will get to explore modern computational techniques for the prediction of materials properties encompassing multi-scale domains. 

I used three tiers of test cases to benchmark the FHI-aims code on the DCC cluster.

1. Small: MD simulation of a 220 atom Ac-Ala19-LysH+ molecule
2. Medium: SCF calculation of a 320 atom periodic Paracetamol structure
3. Large: SCF calculation of a 1648 atom periodic Graphene on SiC(0001) structure

For the larger systems, I needed to carefully gauge and optimize memory allocation to ensure the calculations would complete successfully. To simplify this task, I teamed up with my buddy, ChatGPT to write a script that wraps the SLURM utilities `seff`[^4], `sstat`[^5], and `sacct`[^6] providing a straightforward summary of resource usage for HPC jobs. `sstat` provides resource statistics for currently running jobs while `sacct` is used for completed jobs. `seff` provides information for both ongoing and completed jobs, but is more useful for the latter.  The following sections explain how to use the script and interpret its output. 
# Script

The resource monitoring script, `jobstats.sh` is provided below. 

```bash
#!/usr/bin/env bash

# A script containing functions to parse Slurm job statistics.
# Provides a useful summary of seff, sstat, and sacct.
#
# Usage: jobstats.sh <job_id> [n_steps_for_sacct (optional)]
#
# Authors: Uthpala Herath and ChatGPT

# A function to parse Slurm strings like "7721840K", "5.73M", "186.30M", etc.
# into a byte count. Also handles decimal numbers plus an optional K/M/G suffix.
to_bytes() {
    local val="$1"
    # If empty or not recognized, return 0.
    [[ -z "$val" ]] && echo 0 && return

    # Regex: optionally a decimal number, then optionally K/M/G
    # Examples that match:
    #   "12345" -> no suffix, assume raw bytes
    #   "123.45M"
    #   "186.30M"
    #   "11521316K"
    #   "5.73M"
    if [[ "$val" =~ ^([0-9]+(\.[0-9]+)?)([KMG])?$ ]]; then
        local num="${BASH_REMATCH[1]}"   # e.g. "186.30"
        local unit="${BASH_REMATCH[3]}"  # e.g. "M"
        local factor=1

        case "$unit" in
            K) factor=$((1024)) ;;
            M) factor=$((1024*1024)) ;;
            G) factor=$((1024*1024*1024)) ;;
            *) factor=1 ;;  # no suffix => bytes
        esac

        # We must do a floating-point multiply: num * factor.
        # Use awk to produce an integer result (rounding).
        awk -v n="$num" -v f="$factor" 'BEGIN {
            bytes = n * f
            # round to nearest integer
            printf "%.0f", bytes
        }'
    else
        # If purely integer digits, assume raw bytes
        if [[ "$val" =~ ^[0-9]+$ ]]; then
            echo "$val"
        else
            # Unrecognized format
            echo 0
        fi
    fi
}

# Convert bytes to human-readable MB or GB (switch at 1GB).
to_mb_or_gb() {
    local bytes="$1"
    local oneGB=$((1024*1024*1024))
    if (( bytes < oneGB )); then
        # Show in MB
        awk -v b="$bytes" 'BEGIN { printf "%.2fMB", b/(1024*1024) }'
    else
        # Show in GB
        awk -v b="$bytes" 'BEGIN { printf "%.2fGB", b/(1024*1024*1024) }'
    fi
}

# The main function:
#    - Parse "Nodes: X" from seff output
#    - seff summary
#    - sstat summary (JobID,JobName,MaxRSS,MaxDiskWrite) in MB/GB, plus "Total MaxRSS"
#    - sacct summary (JobID,JobName,MaxRSS,MaxDiskWrite) in MB/GB, plus "Total MaxRSS"
jobstats() {
    local jobid="$1"
    local maxSteps="$2"   # optional second argument

    if [[ -z "$jobid" ]]; then
        echo "Usage: jobstats.sh <job_id> [<n_steps>]"
        return 1
    fi

    # (A) seff output
    local seff_output
    seff_output="$(seff "$jobid" 2>&1)"
    echo "=== [1/3] seff summary ==="
    echo "$seff_output"
    echo

    # Parse "Nodes: X" from seff, if present
    local numNodes
    numNodes="$(echo "$seff_output" | sed -n 's/^Nodes:\s*\([0-9]\+\).*/\1/p')"
    [[ -z "$numNodes" ]] && numNodes=1

    # (B) sstat summary
    echo "=== [2/3] sstat summary (LIVE) ==="
    local sstat_out
    sstat_out="$(
        sstat --noheader --format=JobID%30,MaxRSS,MaxDiskWrite \
              -j "${jobid}" 2>/dev/null
    )"

    if [[ -z "$sstat_out" ]]; then
        echo "Job ${jobid} is not running. Check sacct summary."
    else
        echo "JobID step      | MaxRSS/node | Total MaxRSS | MaxDiskWrite"
        echo "----------------|------------ | ------------ | ------------"
        while IFS= read -r line; do
            [[ -z "$line" ]] && continue
            IFS=' ' read -r stepJobID rawRss rawDisk <<< "$line"
            [[ -z "$stepJobID" ]] && continue

            local rssBytes diskBytes
            rssBytes="$(to_bytes "$rawRss")"
            diskBytes="$(to_bytes "$rawDisk")"

            local rssHuman diskHuman
            rssHuman="$(to_mb_or_gb "$rssBytes")"
            diskHuman="$(to_mb_or_gb "$diskBytes")"

            local totalRSSBytes=$(( rssBytes * numNodes ))
            local totalRSSHuman
            totalRSSHuman="$(to_mb_or_gb "$totalRSSBytes")"

            printf "%-15s | %-11s | %-12s | %s\n" \
                "$stepJobID" "$rssHuman" "$totalRSSHuman" "$diskHuman"
        done <<< "$sstat_out"
    fi
    echo

    # (C) sacct summary
    echo "=== [3/3] sacct summary (WARNING: Inactive until job completion!) ==="
    local sacct_out
    sacct_out="$(
        sacct --noheader \
              --format=JobID%30,JobName%25,MaxRSS,MaxDiskWrite \
              -j "${jobid}" 2>/dev/null
    )"

    if [[ -z "$sacct_out" ]]; then
        echo "No sacct info found."
    else
        # Convert sacct_out into an array so we can optionally truncate
        mapfile -t sacct_lines <<< "$sacct_out"

        # If maxSteps is given and numeric, we tail only last N lines
        if [[ -n "$maxSteps" && "$maxSteps" =~ ^[0-9]+$ ]]; then
            if (( maxSteps < ${#sacct_lines[@]} )); then
                # Truncate to last N lines
                sacct_lines=("${sacct_lines[@]: -$maxSteps}")
            fi
        fi

        echo "JobID step      | JobName                    | MaxRSS/node | Total MaxRSS | MaxDiskWrite"
        echo "----------------|----------------------------|-------------|--------------|-------------"
        for line in "${sacct_lines[@]}"; do
            [[ -z "$line" ]] && continue
            IFS=' ' read -r cJobID cJobName cMaxRSS cMaxDiskWrite <<< "$line"
            [[ -z "$cJobID" ]] && continue

            local rssBytes diskBytes
            rssBytes="$(to_bytes "$cMaxRSS")"
            diskBytes="$(to_bytes "$cMaxDiskWrite")"

            local rssHuman diskHuman
            rssHuman="$(to_mb_or_gb "$rssBytes")"
            diskHuman="$(to_mb_or_gb "$diskBytes")"

            local totalRSSBytes=$(( rssBytes * numNodes ))
            local totalRSSHuman
            totalRSSHuman="$(to_mb_or_gb "$totalRSSBytes")"

            printf "%-15s | %-26s | %-11s | %-12s | %s\n" \
                "$cJobID" "$cJobName" "$rssHuman" "$totalRSSHuman" "$diskHuman"
        done
    fi
}

# Call the function with any arguments passed to the script
jobstats "$@"
```

# Usage

Place this script in a directory which is included in your `$PATH` variable to access it globally (e.g., to make  `/hpc/home/ukh/dotfiles` directory globally accessible, add the line `export PATH="/hpc/home/ukh/dotfiles/:$PATH"`  to your `~/.bashrc` and source it). You may also need to make it executable by typing the following command in the terminal.

```
chmod +x jobstats.sh
```

Now we're all set to use the script to monitor jobs. Say you've submitted a SLURM script for your calculation with `sbatch` and checked its status with `squeue`. You should get something like below. 

```
JOBID     PARTITION NAME             USER  ST     TIME  NODES   NODELIST(REASON)
25623378  courses   paracetamol-5N   ukh   R      0:00  5       dcc-courses-[15,31-34]
```

This job is running on 5 nodes with 84 cores each (with hyper-threading) on the `dcc-courses` partition. I requested 5 GB per cpu with `#SBATCH --mem-per-cpu=5G`, i.e. 2100 GB across all 5 nodes. The quantity `JOBID` is passed as an argument to `jobstats.sh`. 

```
jobstats.sh <JOBID>
```

This gives the output shown below. 

```
$ jobstats.sh 25623378
=== [1/3] seff summary ===
Job ID: 25623378
Cluster: dcc
User/Group: ukh/dukeusers
State: RUNNING
Nodes: 5
Cores per node: 84
CPU Utilized: 00:00:00
CPU Efficiency: 0.00% of 2-08:07:00 core-walltime
Job Wall-clock time: 00:08:01
Memory Utilized: 0.00 MB
Memory Efficiency: 0.00% of 2.05 TB (5.00 GB/core)
WARNING: Efficiency statistics can only be obtained after the job has ended as seff tool is based on the accounting database data.

=== [2/3] sstat summary (LIVE) ===
JobID step      | MaxRSS/node | Total MaxRSS | MaxDiskWrite
----------------|------------ | ------------ | ------------
25623378.0      | 269.17GB    | 1345.87GB    | 175.70MB

=== [3/3] sacct summary (WARNING: Inactive until job completion!) ===
JobID step      | JobName                    | MaxRSS/node | Total MaxRSS | MaxDiskWrite
----------------|----------------------------|-------------|--------------|-------------
25623378        | paracetamol-5N             | 0.00MB      | 0.00MB       | 0.00MB
25623378.batch  | batch                      | 0.00MB      | 0.00MB       | 0.00MB
25623378.extern | extern                     | 0.00MB      | 0.00MB       | 0.00MB
25623378.0      | hydra_bstrap_proxy         | 0.00MB      | 0.00MB       | 0.00MB
```

- `seff` shows partial statistics of the running job, including the number of nodes, cores per node, elapsed time, and requested memory.
- `sacct` is inactive for a running job but lists different job steps.
- `sstat` is most useful here, displaying _current_ memory (`MaxRSS/node` and `Total MaxRSS`) and cumulative I/O usage (`MaxDiskWrite`).

`MaxRSS` (Maximum Resident Set Size) gives the maximum memory used for the job at this instant. Both the per-node (MaxRSS/node) and total (Total MaxRSS) values are displayed here. `MaxDiskWrite` gives the maximum amount of data written to disk at this instant for that job step. The script can be used with the `watch` utility in Unix to monitor real-time resource usage with, 

```
watch -n <interval_in_seconds> jobstats.sh <JOBID>
```

If `Total MaxRSS` exceeds the amount of memory requested for the job (2.05 TB in this case), then the calculation will be terminated with an "Out of Memory" error: 

```
slurmstepd: error: Detected 1 oom_kill event in StepId=25639552.0. Some of the step tasks have been OOM Killed.
srun: error: dcc-courses-28: task 0: Out Of Memory
```

Once the job finishes, the script will also show final statistics under `seff` and `sacct`:

```
$ jobstats.sh 25623378
=== [1/3] seff summary ===
Job ID: 25623378
Cluster: dcc
User/Group: ukh/dukeusers
State: COMPLETED (exit code 0)
Nodes: 5
Cores per node: 84
CPU Utilized: 1-03:31:25
CPU Efficiency: 46.44% of 2-11:16:00 core-walltime
Job Wall-clock time: 00:08:28
Memory Utilized: 1.31 TB
Memory Efficiency: 64.02% of 2.05 TB (5.00 GB/core)
The task which had the largest memory consumption differs by 100.12% from the average task max memory consumption

=== [2/3] sstat summary (LIVE) ===
Job 25623378 is not running. Check sacct summary.

=== [3/3] sacct summary (WARNING: Inactive until job completion!) ===
JobID step      | JobName                    | MaxRSS/node | Total MaxRSS | MaxDiskWrite
----------------|----------------------------|-------------|--------------|-------------
25623378        | paracetamol-5N             | 0.00MB      | 0.00MB       | 0.00MB
25623378.batch  | batch                      | 89.84MB     | 449.20MB     | 1.38MB
25623378.extern | extern                     | 0.25MB      | 1.25MB       | 0.00MB
25623378.0      | hydra_bstrap_proxy         | 269.17GB    | 1345.87GB    | 175.70MB
```

"Memory Utilized" reflects the total memory used for the job which is equivalent to "Total MaxRSS" at the completion of the job. If the job terminates with an insufficient memory problem, request more memory in your SLURM submission script. For optimal resource usage, request sufficient memory while ensuring high "Memory Efficiency" ($\frac{Memory~Utilized}{Memory~Requested}\times100\%$) to make the best of memory resources.

The CPU Efficiency is given by, 

$$
\text {CPU Efficiency}=\frac{\text {CPU Utilized time in seconds}}{(\text {Total no. of CPU cores }) \times(\text {Wall-clock time in seconds})} \times 100 \%
$$

The CPU Utilized time is the *actual* CPU time used by all the processes across all cores. Wall-clock time is the *real* clock time the job spent in the "RUNNING" state. The CPU Efficiency is a measure of *actual* CPU usage vs. total *possible* CPU usage. This job shows a 46.44% CPU Efficiency, which could be improved by lowering the total number of cores used.

The JobID step comprises of different stages of the job process, namely,  
- 25623378 - The top-level parent job record
- 25623378.batch - The “batch” step that typically runs your job script
- 25623378.extern - The “extern” step SLURM uses internally for things like resource allocation
- 25623378.0 - Another job step typically invoked by `srun` (e.g., a MPI task)

Depending on the number of compute steps or sub-processes that may be called within a calculation(s), the JobID step could contain a large number of steps. For such instances, you may truncate the output by passing an argument to `jobstats.sh` with the number of trailing lines to filter the most recent steps with, 

```
jobstats.sh <JobID> <number_of_trailing_lines>
```

For example, `jobstats.sh 1839519 10` shows only the last 10 lines of `sacct`:

```
=== [1/3] seff summary ===
Job ID: 1839519
Cluster: thornyflat
User/Group: ukh0001/its-rc-thorny
State: RUNNING
Nodes: 2
Cores per node: 40
CPU Utilized: 852-16:05:48
CPU Efficiency: 44.23% of 1927-16:30:40 core-walltime
Job Wall-clock time: 24-02:18:23
Memory Utilized: 164.15 GB (estimated maximum)
Memory Efficiency: 0.00% of 16.00 B (8.00 B/node)
WARNING: Efficiency statistics may be misleading for RUNNING jobs.

=== [2/3] sstat summary (LIVE) ===
JobID step      | MaxRSS/node | Total MaxRSS | MaxDiskWrite
----------------|------------ | ------------ | ------------
1839519.658     | 3.74GB      | 7.49GB       | 913.36MB

=== [3/3] sacct summary (WARNING: Inactive until job completion!) ===
JobID step      | JobName                    | MaxRSS/node | Total MaxRSS | MaxDiskWrite
----------------|----------------------------|-------------|--------------|-------------
1839519.649     | wannier90.x                | 561.31MB    | 1.10GB       | 137.15MB
1839519.650     | XHF0.py                    | 108.22MB    | 216.44MB     | 435.06MB
1839519.651     | dmft.x                     | 434.59MB    | 869.19MB     | 36.82MB
1839519.652     | ctqmc                      | 225.77MB    | 451.54MB     | 0.01MB
1839519.653     | ctqmc                      | 218.11MB    | 436.21MB     | 2.51MB
1839519.654     | ctqmc                      | 220.24MB    | 440.48MB     | 2.51MB
1839519.655     | ctqmc                      | 229.46MB    | 458.93MB     | 2.53MB
1839519.656     | ctqmc                      | 230.46MB    | 460.91MB     | 2.54MB
1839519.657     | ctqmc                      | 220.06MB    | 440.12MB     | 2.54MB
1839519.658     | vaspDMFT                   | 0.00MB      | 0.00MB       | 0.00MB
```

This tells us that `vaspDMFT` is the currently active step in the job process. 

I hope this script helps you monitor and optimize your HPC jobs more effectively. Let me know in the comments if it works for you.
# References

[^1]: [https://oit-rc.pages.oit.duke.edu/rcsupportdocs](https://oit-rc.pages.oit.duke.edu/rcsupportdocs)
[^2]: [https://fhi-aims.org](https://fhi-aims.org)
[^3]: [https://graduateschool.bulletins.duke.edu/courses/0261981](https://graduateschool.bulletins.duke.edu/courses/0261981)
[^4]: [https://support.schedmd.com/show_bug.cgi?id=1611](https://support.schedmd.com/show_bug.cgi?id=1611)
[^5]: [https://slurm.schedmd.com/sstat.html](https://support.schedmd.com/show_bug.cgi?id=1611)
[^6]: [https://slurm.schedmd.com/sacct.html](https://slurm.schedmd.com/sacct.html)
