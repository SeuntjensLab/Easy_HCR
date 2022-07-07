# Easy_HCR

This is a set of jupyter notebooks made to automate the creation of probe pairs for hybridization chain reactions (HCR). It relies and is heavily based on [insitu_probe_generator](https://github.com/rwnull/insitu_probe_generator) by Ryan Null.

If this notebook is helpful for your research, please cite the following preprint and also the probe generator made by the Özpolat lab:

Elagoz, A. M., Styfhals, R., Maccuro, S., Masin, L., Moons, L., & Seuntjens, E. (2022). Optimization of Whole Mount RNA Multiplexed in situ Hybridization Chain Reaction With Immunohistochemistry, Clearing and Imaging to Visualize Octopus Embryonic Neurogenesis. Frontiers in Physiology, 995.

Kuehn, E., Clausen, D. S., Null, R. W., Metzger, B. M., Willis, A. D., & Özpolat, B. D. (2021). Segment number threshold determines juvenile onset of germline cluster expansion in Platynereis dumerilii. Journal of Experimental Zoology Part B: Molecular and Developmental Evolution. https://doi.org/10.1002/jez.b.23100


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

These will be automatically installed if you follow the installation guide below

# Installation
Depending on your needs, to fully automate the process you need to install BLAST on your local computer. Download the windows 64x file: ncbi-blast-2.12.0+-win64.exe  
https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/

We recommend installing all the required dependencies through [Miniconda](https://docs.conda.io/en/latest/miniconda.html), allowing the script to run inside a dedicated environment without interfering or causing conflicts with the host computer.
After installing Miniconda, open Anaconda Prompt (on Windows) or a terminal on Linux and macOS

Navigate inside the downloaded folder containing the script by using the following command on Windows

    cd /d *replace this with the full path of the folder*

Or the following command on macOS and Linux

    cd *replace this with the full path of the folder*

Then we need to create an environment in which the script will. This can be done by running the following command

    conda env create -f hcr.yml
    
To check if BLAST is correctly installed run

    blastn



# Usage
**NOTE: All of the following commands should be run from inside the folder of the script**. Check the first step of the installation on how to do it.

To activate the environment and launch jupyter, run the following commands

    conda activate HCR
    jupyter notebook

Here you can launch the notebook you need!

# Custom database creation

Prepare your fasta file of your species of interest and follow the guidelines listed in the notebook: custom_database_creation.ipynb
