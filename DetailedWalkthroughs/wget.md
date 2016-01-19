# Using `wget` to Download Sequence Files

#### Notebook Setup

1. First, create a directory for your project sequences in the `/var/seq_data/` directory on the server
  * Use the naming scheme `/var/seq_data/PROJECT_NAME/` with any subdirectories for individual sections or runs for your project
1. Next, setup the `$seqDir` variable in your notebook and prepare for doanloading sequences.
   
  ```r
seqDir = '/var/seq_data/PROJECT_NAME/SUBDIRECTORY' 
  ```
   
  ```r
if not os.path.isdir(seqDir):  
     os.makedirs(seqDir)
  ```

#### Download Sequence and Index Files
###### Read1
```r
!cd $seqDir; \
    wget -O read1.fq.gz \
    "LINK_TO_READ1_FILE_DOWNLOAD"
```

###### Read2
```r
!cd $seqDir; \
    wget -O read2.fq.gz \
    "LINK_TO_READ2_FILE_DOWNLOAD"
```

###### Index1
```r
!cd $seqDir; \
    wget -O index1.fq.gz \
    "LINK_TO_INDEX1_FILE_DOWNLOAD"
```

###### Index2
```r
!cd $seqDir; \
    wget -O index2.fq.gz \
    "LINK_TO_INDEX2_FILE_DOWNLOAD"
```
