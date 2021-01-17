1. `rm -r backup`
2. `cp SRR098026.fastq SRR098026-backup.fastq` and `cp SRR097977.fastq SRR097977-backup.fastq`
3. `mkdir backup` and `mv *-backup.fastq backup`
4. `chmod -w backup/*-backup.fastq`

It’s always a good idea to check your work with `ls -l backup`. You should see something like:

```
-r--r--r-- 1 ubuntu ubuntu 47552 Jan 17 23:37 SRR097977-backup.fastq
-r--r--r-- 1 ubuntu ubuntu 43332 Jan 17 23:37 SRR098026-backup.fastq
```
