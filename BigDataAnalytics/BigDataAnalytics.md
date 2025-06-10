# Big Data Analytics


## HDFS

### What is HDFS?
- HDFS stands for Hadoop Distributed File System.
- It is designed to store large data sets reliably and to stream those data sets at high bandwidth to user applications.
- The default block size in HDFS is 64MB, which means that files are divided into blocks of at least 64MB in size.
- This default 64MB size can be changed and increased in multiples of 64MB by hadoop administrator.


### NameNode
- The NameNode is the master server in the HDFS architecture.
- Client machine communicates with the Name node.
- It is responsible for managing the file system namespace and regulating access to files by clients.
- All metadata operations—such as opening, closing, renaming files and directories—are handled by the NameNode.
- NameNode does not store the actual data; it only stores the metadata about file locations, block mappings, and replication details.

#### For what all purposes client machine communicates directly with the NameNode?
The client machine communicates directly with the NameNode to -
- Retrieve metadata (e.g., block locations),
- Request file system operations,
- Initiate reads and writes (data transfer is handled separately by DataNodes).

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