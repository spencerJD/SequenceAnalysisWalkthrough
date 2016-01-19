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
Next, we must uncompress the sequence read files in order to merge them with `PEAR`

```python
glob(os.path.join(seqDir, 'read?.fq'))
```

```r
uncompFiles = glob(os.path.join(seqDir, 'read?.fq'))

if len(uncompFiles) != 2:
    !cd $seqDir; \
        pigz -k -d -p 24 read?.fq.gz
```


