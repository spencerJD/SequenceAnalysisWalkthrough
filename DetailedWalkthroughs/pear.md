#Merging Raw Reads with `PEAR` and Creating Screed Databases
This walkthrough will lead you through the creation and implementation of a Jupyter notebook to merge raw reads with `PEAR` and create screed database files needed for downstream applications. 


###Set Variables
First, you must set the file variables for `PEAR`
```r
seqDir = '/var/seq_data/PROJECT_NAME/'

readFile1 = 'read1.fq.gz'
readFile2 = 'read2.fq.gz'
```

###Initialization for Notebook
Next, you must initialize your notebook with all needed libraries. 

```python
import screed
from glob import glob
import matplotlib.pyplot as plt
from mpltools import style
import numpy as np
from mpld3 import enable_notebook
import screed
```

```python
%matplotlib inline  
%load_ext rpy2.ipython
```

```python
%%R
library(ggplot2)
library(dplyr)
```

###Uncompressing Read Files
Next, we must uncompress the sequence read files in order to merge them with `PEAR`. The following code will uncompress both of your Read1 and Read2 files.

```python
glob(os.path.join(seqDir, 'read?.fq'))
```

```r
uncompFiles = glob(os.path.join(seqDir, 'read?.fq'))

if len(uncompFiles) != 2:
    !cd $seqDir; \
        pigz -k -d -p 24 read?.fq.gz
```

At this point, your read files will be uncompressed and you can proceed with `PEAR` merging.

###Merging Reads with `PEAR`
We use `PEAR` to combine our Read1 and Read2 fastq files into one file with an updated quality score based on the overlapping region of the two reads. This combined sequence is used in all downstream applications.

In addition to the required `-f` (forward read), `-r` (reverse read), and `-o` (output file name base), we use the `-m` (maximum assembled read length) and `-j` (number of threads) command line arguments. The `$(date +%F)` portion of the `-o` argument returns the current date as part of the naming scheme for all output files.

```r
!cd $seqDir; \
    pear -m 600 -j 8 \
    -f read1.fq \
    -r read2.fq \
    -o pear_merged-$(date +%F)
```

Running this command will result in 4 output files:  
    * Assembled reads file  
    * Discarded reads file  
    * Unassembled forward reads file  
    * Unassembled reverse reads file  

We will be concerned mostly with the assembled reads file for downstream applications.

###Make a Screed Database of Merged Reads
A screed database contains sequence information such as sequence name, sequence quality, and the sequence itself in an easily queried format. We will create a screed database using our merged reads for downsream applications.

* Create the screed database
     ```r
pear_merged_file = !echo "pear_merged-"$(date +%F)".assembled.fastq"
pear_merged_file = pear_merged_file[0]

os.chdir(seqDir)
screed.read_fastq_sequences(pear_merged_file)

pear_merged_file += '_screed'
fqdb = screed.ScreedDB(pear_merged_file)
     ```

* Check the lengths of the sequences in your merged sequences file

     ```r
lengths = []
for read in fqdb.itervalues():
    lengths.append((len(read["sequence"])))
     ```

* Plot a histogram to visually check sequence lengths

     ```r
style.use("ggplot")
fig = plt.figure()
ax = fig.add_subplot(111)
h = ax.hist(np.array(lengths), bins=50)
xl = ax.set_xlabel("Sequence Length, nt")
yl = ax.set_ylabel("Count")
fig.set_size_inches((10,6))
     ```

  * Example Output:
![Sequence Length Histogram](https://cloud.githubusercontent.com/assets/7449496/12431718/03052300-bec5-11e5-871b-b782c7c3c64c.png)





