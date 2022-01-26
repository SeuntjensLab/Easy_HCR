# easy_hcr

This is a set of jupyter notebooks made to automate the creation of probe pairs for hybridization chain reactions (HCR). It relies and is heavily based on [insitu_probe_generator](https://github.com/rwnull/insitu_probe_generator) by Ryan Null

If this notebook is helpfull for your research please cite the following preprint:
Elagoz, A. M. et al. Optimization of Whole Mount RNA multiplexed in situ Hybridization Chain Reaction with Immunohistochemistry, Clearing and Imaging to visualize octopus neurogenesis. In preparation. (2022).

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
We recommend installing all the required dependencies through [Miniconda](https://docs.conda.io/en/latest/miniconda.html), allowing the script to run inside a dedicated environment without interfering or causing conflicts with the host computer.
After installing Miniconda, open Anaconda Prompt (on Windows) or a terminal on Linux and macOS

Navigate to inside the downloaded folder containing the script by using the following command on Windows

    cd /d *replace this with the full path of the folder*

Or the following command on macOS and Linus

    cd *replace this with the full path of the folder*

Then we need to create an enviroinment in which the script will. This can be done by running the following command

    conda env create -f hcr.yml

Depending on your needs, to fully automate the process you need to install blast on your local computer. Download the windows 64x file 
https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/
To check check if blast is correctly installed run

    blastn


# Usage
**NOTE: All of the following commends should be run from inside the folder of the script**. Check the first step of the installation on how to do it

To activate the environment and launch jupyter, run the following commands

    conda activate HCR
    jupyter notebook

Here you can launch the notebook you need!
