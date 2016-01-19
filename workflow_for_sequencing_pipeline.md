#Workflow for Sequencing Pipeline

##Downloading Links to Sequences

* First, you will receive an email from Peter Schweitzer with links to your sequences.
* Expect 4 files in Peter's email:
  * Forward Indices
  * Reverse Indicies
  * Forward Reads
  * Reverse Reads
* Using `wget`, download your files to the sequence directory on the server.
  * [Detailed walkthrough for wget](./DetailedWalkthroughs/wget.md)


#####File Management
Normally, sequence files should be downloaded to the `/var/seqdata/PROJECT_NAME` directory on the server, with `PROJECT_NAME` replaced by your project's title.

You should expect 4 files in Peter's email:
* Forward Indices
* Reverse Indicies
* Forward Reads
* Reverse Reads

Reads and indicies are listed in the same order in each file. That is, the first sequences in the Forward and Reverse Indicies files correspond to the first sequences in each the Forward and Reverse read files.


## Merge Sequences Together 




