# Big Data Analytics


## HDFS

### What is HDFS?
- Minimum size 64MB

### Name Node

### What is FSImage (File table)?
- Where the blocks of original files are going to be stored
- Imagine this like a index page of a book showing which topics are on which page number

### What is Hadoop cluster?
- Hadoop cluster is deployed in a production environment in multiple racks.

### What is Replication Factor?
- System wide default replication factor is 3
- Suppose one saves 1GB file in HDFS, then this file will be replicated 3 times, meaning actually it will be occupying
3GB of space. This is because each node saving a part of file will be replicated 3 times. This replication is required
to avoid data corruption in even of any failures.