# Using `wget` to Download Sequence Files

## Notebook Setup

1. First, create a directory for your project sequences in the `/var/seq_data/` directory on the server
  * Use the naming scheme `/var/seq_data/PROJECT_NAME/` with any subdirectories for individual sections or runs for your project
1. Next, setup the `$seqDir` variable in your notebook and prepare for doanloading sequences.
   
  ```python
seqDir = '/var/seq_data/PROJECT_NAME/SUBDIRECTORY' 
  ```
   
  ```python
if not os.path.isdir(seqDir):  
     os.makedirs(seqDir)
  ```

