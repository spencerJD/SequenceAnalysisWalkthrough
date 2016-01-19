#Workflow for Sequencing Pipeline

##Downloading Links to Sequences

* First, you will receive an email from Peter Schweitzer with links to your sequences.
* SSH into the server and navigate to the directory where you want your sequence files.
* Type the following: `w3m http://www.google.com`
* Type `SHIFT + U`, which opens an input message for a direct link.
* Copy and paste the first link from Peter's email, and hit `ENTER`. 
* Repeat for all remaining links.
  * NOTE: You can rename the files as you download them by modifying the names as they are downloaded.
* When all files are downloaded, you can exit the w3m browser by typing `q` and then `y` at the prompt.
* Unzip the Forward and Reverse Read files using `gunzip FILE_NAME`

#####File Management
Normally, sequence files should be downloaded to the `/var/seqdata/PROJECT_NAME` directory on the server, with `PROJECT_NAME` replaced by your project's title.

You should expect 4 files in Peter's email:
* Forward Indices
* Reverse Indicies
* Forward Reads
* Reverse Reads

Reads and indicies are listed in the same order in each file. That is, the first sequences in the Forward and Reverse Indicies files correspond to the first sequences in each the Forward and Reverse read files.


## Merge Sequences Together 




