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

NOTE: At this point, raw read QC analysis can be performed. Refer to the `raw_read_QC` Jupyter Notebook in the `fullCyc` dataset for these commands.

## Merge Sequences Together 

* `PEAR` is used to merge sequences from Read1 and Read2 together, while updating the quality scores of bases based on the overlapping region.
* First, we run `PEAR` in order to merge reads 1 and 2 together.
* Then we create a screed database to allow to fast access to information about the merged sequences (length, quality, etc.)
* Finally we run basic quality statistics regarding the quality scores of our sequences. 

[Detailed Walkthrough for `PEAR`](./DetailedWalkthroughs/pear.md)




