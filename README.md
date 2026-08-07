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

## Table of Contents  
- [Installation](#installation)
  - [First time](#first-time)
  - [Already installed once](#already-installed-once)
- [Usage](#usage)
  - [*Octopus vulgaris*](#octopus-vulgaris)
    - [1. Create custom databases](#1-create-the-necessary-custom-databases)
    - [2. Run Easy_HCR](#2-run-easy_hcr)
  - [*Pomacea canaliculata*](#pomacea-canaliculata-apple-snail)
    - [1. Create custom databases](#1-create-custom-databases)
    - [2. Run Easy_HCR](#2-run)
  - [*Other organisms*](#other-organisms)
    - [1. Gather necessary files](#1-gather-necessary-files)
    - [2. Create custom databases](#2-create-custom-databases)
    - [2. Run Easy_HCR](#3-run)

## Installation

### First time
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

### Already installed once

For those who already followed the installation steps once, you need to first uninstall Blast and install the newest version, rename your old Easy_HCR folder and then install the new environment using:

- Uninstall Blast:
    - Go in drive C > Programs > NCBI > blast-...+
    - Double click on Uninstall-ncbi-blast-...+
    - Follow the installation instructions of Blast [here](#installation)
- Move to your working directory:

    ```
    cd Documents/Github
    ```

- Change the name of the old folder:
    
    ```
    mv Easy_HCR/ Easy_HCR_old/
    ```

- Clone again the Easy_HCR github repository and navigate to it

    ```
    git clone https://github.com/SeuntjensLab/Easy_HCR.git
    cd Easy_HCR
    ```

- Remove the old conda environment and create the new one:

    ```
    conda remove -n HCR --all
    conda env create -f hcr.yml
    ```

## Usage
> [!IMPORTANT]
> **All of the following commands should be run from inside the folder of the script.**

To activate the environment and launch jupyter, run the following commands

    conda activate HCR
    jupyter notebook

This will open a window in your web browser and you can then click on the notebook you need to open it and then run the commands.

### *Octopus vulgaris*

#### 1. Create the necessary custom databases

You will need to **prepare the different fasta files** using the [custom_database_creation.ipynb](custom_database_creation.ipynb) jupyter notebook. You can just follow the instructions in the notebook.

You need to **run this notebook ones per fasta file** and it can be run directly on the compressed files (finishing with extension .gz). 

The different fasta files on which you need to run this script are present in the folder `necessary_files` except for the genome of *vulgaris*:
- [Transcriptome](necessary_files/xcOctVulg1.1_MT_mergedPeaks_CDS.fa.gz) of *O. vulgaris*
- [Genome](necessary_files/GCF_006345805.1_ASM634580v1_rna.fna.gz) of *O. sinensis*

The genome of *O. vulgaris* can be downloaded [**here**](https://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/951/406/725/GCA_951406725.2_xcOctVulg1.2/GCA_951406725.2_xcOctVulg1.2_genomic.fna.gz).

Once it's downloaded you can place it in the `necessary_files` folder on your computer and then run the jupyter notebook.

#### 2. Run Easy_HCR

You can choose to run either the [**old version**](HCR_probe_QC_octopus.ipynb) of the script, which will map the probes **only against the *O. vulgaris* transcriptome** for quality check, or the [new version](HCR_probe_QC_octopus_modified_by_Enora.ipynb) improved by Enora Geslain. This **new version** will map the probe pairs (PP) **against the *O. vulgaris* transcriptome but also against the *O. vulgaris* and *O. sinensis* genomes** for the quality check. For both scripts, you can just follow the instructions in the notebook.

The new version also gives the possibility to map the PP only against the *O. vulgaris* transcriptome.

### *Pomacea canaliculata* (apple snail)

#### 1. Create custom databases

You will need to **prepare the different fasta files** using the [custom_database_creation.ipynb](custom_database_creation.ipynb) jupyter notebook. You can just follow the instructions in the notebook.

You need to **run this notebook ones per fasta file** and it can be run directly on the compressed files (finishing with extension .gz). 

The different fasta files on which you need to run this script are present in the folder `necessary_files` except for the genome of *pomacea*:
- [Transcriptome](necessary_files/GCF_003073045.1_ASM307304v1_cds_from_genomic.fna.gz) of *P. canaliculata*

The genome of *P. canaliculata* can be downloaded [**here**](https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/003/073/045/GCF_003073045.1_ASM307304v1/GCF_003073045.1_ASM307304v1_genomic.fna.gz).

Once it's downloaded you can place it in the `necessary_files` folder on your computer and then run the jupyter notebook.

#### 2. Run

You need to run the [**script**](HCR_probe_QC_apple-snail.ipynb) to generate probe pairs (PP) and map them against, first, the ***P. canaliculata* transcriptome** and then the ***P. canaliculata* whole genome** for quality check. To run the script, you can just follow the instructions in the notebook.

### Other organisms

If you want to run the modified version from Enora on another organism to check the efficiency of your probes you can follow these steps

#### 1. Gather necessary files

First of all, you will need to download the necessary files for your target species. To be able to run this modified version you need a well annotated reference genome and you need to gather the following files:

  - **FASTA file** of your reference **genome**
  - **GTF file** of your reference **genome**
  - **FASTA file** file containing your reference **transcriptome**

#### 2. Create custom databases

When you have gathered all these files, you need to **prepare the fasta files** using the [custom_database_creation.ipynb](custom_database_creation.ipynb) jupyter notebook. You can just follow the instructions in the notebook.

You need to **run this notebook once per fasta file** and it can be run directly on the compressed files (finishing with extension .gz).

#### 3. Run

To run Easy_HCR on your target species, you need to use [**this script**](HCR_probe_QC_other.ipynb) to generate probe pairs (PP) and map them against, first, the **transcriptome** of your species and then the **whole genome** for quality check. To run the script, you will need to adjust some parts:

  - **cell 13** of the jupyter notebook: put the **correct GTF file** name
  - **cell 15** of the jupyter notebook: put the **correct transcriptome** FASTA file name
  - **cell 27** of the jupyter notebook: put the **correct genome** FASTA file name