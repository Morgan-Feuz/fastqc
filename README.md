# Fastq File Quality Control with FastQC


### Background
One of the first steps in RNA-sequencing (RNA-seq) analysis is to perform a quality assessment of sample fastq files to check for possible sequencing issues that may need addressed prior to further downstream analysis. A popular tool for this purpose is [FastQC](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/). 

---------------------------------------------------------

### Installation and Set-up on Linux

Refer to the [FastQC installation guide](https://raw.githubusercontent.com/s-andrews/FastQC/master/INSTALL.txt) for additional instructions and to install appropriately on Windows/OSX.

1 - FastQC requires a suitable Java Runtime Environment (JRE) to be installed to run properly. Most Linux distributions will already have Java installed already. 
```
# Ubuntu/Mint: Check Java Version
$ java -version

# Install JRE if necessary
$ sudo apt install default-jre
```

2 - Download the most recent version/installation of FastQC (v0.12.1) and unzip the file in a suitable location.

```
$ unzip fastqc_v0.12.1.zip
```

3 - Per the installation guide, there is a wrapper script called `fastqc`, which is the easiest way to start the program and can be found in the top level of the FastQC installation. Use `chmod 755` to allow read, write, and execute permissions to the owner of the file. 

```
# Make the file executable (make sure to specify the right file location)
$ sudo chmod 755 path/to/file/fastqc
```

Now, FastQC can either be ran as a interactive graphical application (`./fastqc` to open the program) or non-interactively via the command line. 

```
# Make fastqc executable from any location
## Create a symbolic link to the bin
$ sudo ln -s /path/to/file/fastqc /usr/local/bin/fastqc

# check the link
$ fastqc -v
```
----------------------------------------------------------------------------------------------------------------------

### Usage
1 - Single fastq file example. Note that FastQC will output the report files to the current directory if one is not specified. By default, FastQC will create an HTML report with corresponding graphs as well as a zip file (not extracted by default) containing individual graph other data files. 
```
# Run Fastqc on a single file
$ fastqc /path/to/file/fastq_R1_001.fastq.gz
```

2 - Analyze all files in a directory with specified output directory. 
```
# Run fastqc on multiple files
$ fastqc /path/to/file/*.fastq.gz* --outdir=/path/to/file
```
3 - [MultiQC](https://multiqc.info/) can be used to combine individual FastQC reports/graphs into combined graphs. 
```
# Navigate to directory with FastQC reports then run MultiQC
$ multiqc . 
```

------------------------------------------------------------------------------------------------------------------

### Analysis Interpretation
Currently, the FastQC analysis modules are: 
+ Basic Statistics
+ Per Base Sequence Quality
+ Per Sequence Quality Scores
+ Per Sequence GC Content
+ Per Base Sequence Content
+ Per Base N Content
+ Sequence Length Distribution
+ Duplicate Sequences
+ Overrepresented Sequences
+ Adapter Content
+ Kmer Content
+ Per Tile Sequence Quality

Detailed information regarding interpretation of the FastQC reports can be found [here](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/Help/3%20Analysis%20Modules/). 

-----------------------------------------------------------------------------------------------------------------
