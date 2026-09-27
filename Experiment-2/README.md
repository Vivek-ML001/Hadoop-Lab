
# Experiment 2 — Hadoop HDFS File Management

##  Aim

To implement basic file management operations in Hadoop HDFS:

- Adding files and directories
- Retrieving files
- Deleting files

---

##  Technologies Used

- **Apache Hadoop 3.3.6**
- **HDFS (Hadoop Distributed File System)**
- **Windows 10**
- **Java 8**
- Command Prompt (CMD)

---

##  Hadoop Services Used

The Hadoop pseudo-distributed cluster was started using:

```cmd
start-dfs.cmd
start-yarn.cmd
````

The running Hadoop services were verified using:

```cmd
jps
```

Expected output:

```text
NameNode
DataNode
ResourceManager
NodeManager
Jps
```

### Services

| Service         | Purpose                           |
| --------------- | --------------------------------- |
| NameNode        | Manages HDFS metadata             |
| DataNode        | Stores actual HDFS data           |
| ResourceManager | Manages cluster resources         |
| NodeManager     | Manages tasks/resources on a node |

---

# 1. Adding Directories

A directory named `experiment2` was created in HDFS.

```cmd
hdfs dfs -mkdir /vivek/experiment2
```

A `data` subdirectory was then created:

```cmd
hdfs dfs -mkdir /vivek/experiment2/data
```

The directory contents were verified using:

```cmd
hdfs dfs -ls /vivek/experiment2
```

Expected output:

```text
data
```

---

# 2. Creating a Local File

A sample text file was created on the local Windows filesystem.

```cmd
echo Hadoop is a distributed file system. > sample.txt
echo HDFS stores large files across DataNodes. >> sample.txt
echo NameNode manages HDFS metadata. >> sample.txt
```

The contents were checked using:

```cmd
type sample.txt
```

Output:

```text
Hadoop is a distributed file system.
HDFS stores large files across DataNodes.
NameNode manages HDFS metadata.
```

---

# 3. Uploading a File to HDFS

The local file was uploaded to HDFS using the `-put` command:

```cmd
hdfs dfs -put sample.txt /vivek/experiment2/data/
```

The uploaded file was verified using:

```cmd
hdfs dfs -ls /vivek/experiment2/data
```

Expected output:

```text
sample.txt
```

### File Transfer

```text
Local Windows File
       |
       | hdfs dfs -put
       ↓
      HDFS
       |
/vivek/experiment2/data/sample.txt
```

---

# 4. Retrieving a File from HDFS

The contents of the HDFS file were displayed using:

```cmd
hdfs dfs -cat /vivek/experiment2/data/sample.txt
```

The file was also downloaded from HDFS to the local filesystem:

```cmd
hdfs dfs -get /vivek/experiment2/data/sample.txt retrieved.txt
```

The downloaded file was verified using:

```cmd
type retrieved.txt
```

### File Retrieval

```text
HDFS
 |
 | hdfs dfs -get
 ↓
Windows Local Filesystem
 |
retrieved.txt
```

---

# 5. Deleting a File

The HDFS file was deleted using:

```cmd
hdfs dfs -rm /vivek/experiment2/data/sample.txt
```

The directory was checked again:

```cmd
hdfs dfs -ls /vivek/experiment2/data
```

The file was no longer present.

---

# 6. Deleting a Directory

After deleting the file, the empty `data` directory was removed:

```cmd
hdfs dfs -rmdir /vivek/experiment2/data
```

Finally, the `experiment2` directory was removed:

```cmd
hdfs dfs -rmdir /vivek/experiment2
```

---

#  Important HDFS Commands

| Operation              | Command                               |
| ---------------------- | ------------------------------------- |
| Create directory       | `hdfs dfs -mkdir /path`               |
| List files/directories | `hdfs dfs -ls /path`                  |
| Upload file            | `hdfs dfs -put local_file /hdfs/path` |
| Download file          | `hdfs dfs -get /hdfs/file local_file` |
| Display file           | `hdfs dfs -cat /hdfs/file`            |
| Delete file            | `hdfs dfs -rm /hdfs/file`             |
| Delete empty directory | `hdfs dfs -rmdir /hdfs/directory`     |
| Delete recursively     | `hdfs dfs -rm -r /hdfs/directory`     |

---

#  Complete Workflow

```text
Create Directory
       ↓
Create Local File
       ↓
Upload File to HDFS
       ↓
Verify File
       ↓
Read File using -cat
       ↓
Download File using -get
       ↓
Delete HDFS File
       ↓
Delete Directory
```

---

#  Concepts Learned

Through this experiment, the following HDFS concepts were practiced:

* HDFS directory creation
* Local-to-HDFS file transfer
* HDFS-to-local file transfer
* Listing HDFS contents
* Reading files stored in HDFS
* File deletion
* Directory deletion
* Basic HDFS command-line operations

---

#  Result

The basic file management operations in **Hadoop HDFS** were successfully implemented, including:

1. Adding files and directories
2. Retrieving files from HDFS
3. Deleting files and directories

---

##  Author

**Vivek**

B.Tech — Computer Science & Engineering (Machine Learning)

Gautam Buddha University