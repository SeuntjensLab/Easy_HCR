# Easy_HCR

This is a set of jupyter notebooks made to automate the creation of probe pairs for hybridization chain reactions (HCR). It relies and is heavily based on [insitu_probe_generator](https://github.com/rwnull/insitu_probe_generator) by Ryan Null. 

If this notebook is helpful for your research, please cite our paper and also the probe generator made by the Özpolat lab:

Elagoz, A. M., Styfhals, R., Maccuro, S., Masin, L., Moons, L., & Seuntjens, E. (2022). Optimization of Whole Mount RNA Multiplexed in situ Hybridization Chain    Reaction With Immunohistochemistry, Clearing and Imaging to Visualize Octopus Embryonic Neurogenesis. Frontiers in Physiology, 995.     https://www.frontiersin.org/articles/10.3389/fphys.2022.882413/full

Kuehn, E., Clausen, D. S., Null, R. W., Metzger, B. M., Willis, A. D., & Özpolat, B. D. (2021). Segment number threshold determines juvenile onset of germline  cluster expansion in Platynereis dumerilii. Journal of Experimental Zoology Part B: Molecular and Developmental Evolution. https://doi.org/10.1002/jez.b.23100


These notebooks feature
+ Automated blasting and probe pair filtering to minimize off-target effects
+ Blasting on custom databases
+ Probe list formatting for easy ordering from IDT

This notebook has the following dependencies.
Make sure that these are installed in your environment when you launch this notebook.
+ pandas
+ biopython
+ numpy
+ openpyxl

These will be automatically installed if you follow the installation guide below.

### Table of Contents  
- [Installation](#installation)
- [Usage](#usage)
  - [1. Create custom databases](#1-create-the-necessary-custom-database)
  - [2. Run Easy_HCR](#2-run-easy_hcr)

## Installation
The first step to fully automate the process is to install BLAST on your local computer.
Download the windows 64x file: ncbi-blast-2.17.0+-win64.exe
https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/

We recommend installing all the required dependencies through [Miniconda](https://docs.conda.io/en/latest/miniconda.html), allowing the script to run inside a dedicated environment without interfering or causing conflicts with the host computer.
After installing Miniconda, open Anaconda Prompt (on Windows) or a terminal on Linux and macOS

Navigate to a suitable working directory by using the following command on Windows:

    cd *replace this with the full path of the folder*
    (example: cd Documents/Github)

Or the following command on macOS and Linux

    cd *replace this with the full path of the folder*

After that you need to download the Github repository and navigate in it using the commands:

    git clone https://github.com/SeuntjensLab/Easy_HCR.git
    cd Easy_HCR

Then you need to create a conda environment containing all the necessary dependencies. This can be done by running the following command:

    conda env create -f hcr.yml
    
To check if BLAST is correctly installed run

    blastn -version

You should see the following output:

    blastn: 2.17.0+
     Package: blast 2.17.0, build Jul  1 2025 08:57:20

For those who already followed the installation steps once, you need to first uninstall Blast and install the newest version, rename your old Easy_HCR folder and then install the new environment using:

    # Uninstall Blast
    # Go in drive C > Programs > NCBI > blast-...+
    # Double click on Uninstall-ncbi-blast-...+
    # You can then follow the installation instructions of Blast [here](#installation)
    # Move to your working directory
    cd Documents/Github
    # Change the name of the old folder
    mv Easy_HCR/ Easy_HCR_old/
    # Clone again the Easy_HCR github repository and navigate to it
    git clone https://github.com/SeuntjensLab/Easy_HCR.git
    cd Easy_HCR
    # Remove the old conda environment
    conda remove -n HCR --all
    # Create a new conda environment
    conda env create -f hcr.yml

## Usage
> [!IMPORTANT]
> **All of the following commands should be run from inside the folder of the script.**

To activate the environment and launch jupyter, run the following commands

    conda activate HCR
    jupyter notebook

This will open a window in your web browser and you can then click on the notebook you need to open it and then run the commands.

### 1. Create the necessary custom database

You will need to **prepare the different fasta files** using the [custom_database_creation.ipynb](custom_database_creation.ipynb) jupyter notebook. You can just follow the instructions in the notebook.

You need to **run this notebook ones per fasta file** and it can be run directly on the compressed files (finishing with extension .gz). 

The different fasta files on which you need to run this script are present in the folder `necessary_files` except for the genome of *vulgaris*:
- [Transcriptome](necessary_files/xcOctVulg1.1_MT_mergedPeaks_CDS.fa.gz) of *O. vulgaris*
- [Genome](necessary_files/GCF_006345805.1_ASM634580v1_rna.fna.gz) of *O. sinensis*

The genome of *O. vulgaris* can be downloaded [**here**](https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/951/406/725/GCA_951406725.2_xcOctVulg1.2/GCA_951406725.2_xcOctVulg1.2_genomic.fna.gz).

Once it's downloaded you can place it in the `necessary_files` folder on your computer and then run the jupyter notebook.

### 2. Run Easy_HCR

You can choose to run either the [**old version**](HCR_probe_QC_octopus.ipynb) of the script, which will map the probes **only against the *O. vulgaris* transcriptome** for quality check, or the [new version](HCR_probe_QC_octopus_modified_by_Enora.ipynb) improved by Enora Geslain. This **new version** will map the probe pairs (PP) **against the *O. vulgaris* transcriptome but also against the *O. vulgaris* and *O. sinensis* genomes** for the quality check. For both scripts, you can just follow the instructions in the notebook.

The new version also gives the possibility to map the PP only against the *O. vulgaris* transcriptome.
