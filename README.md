# Ligand-library-curation-and-blind-docking

# Ligand Library Preparation

## Overview

This guide provides step-by-step instructions to prepare a ligand library using the ZINC database, process files using PowerShell, and utilize Open Babel for various molecular manipulations.

## Steps

### 1. Download Ligands from ZINC Database

1. **Access the ZINC Database:**
   - Go to [ZINC Database](https://zinc.docking.org/).

2. **Filter Ligands:**
   - Apply filters for 3D structures and other desired parameters.

3. **Download Ligands:**
   - Download the ligands in SDF format.
   - Ensure to unselect the "flat" option.
   - Download the tranches into a directory.

### 2. Process Files Using PowerShell

1. **Rename Files:**
   - Change the extension of the downloaded files to `.ps1` (e.g., `ligands.ps1`).

2. **Open PowerShell:**
   - Move to the directory containing the `.ps1` file.

3. **Set Execution Policy:**
   - Run the following command to allow script execution:
     ```sh
     Set-ExecutionPolicy Unrestricted
     ```
   - Select "Yes to all".

4. **Run the Script:**
   - Execute the script:
     ```sh
     ./ligands.ps1
     ```

5. **Reset Execution Policy:**
   - Reset the execution policy to restricted:
     ```sh
     Set-ExecutionPolicy Restricted
     ```

### 3. Extract Files

1. **Extract `.gz` Files:**
   - Go to the working directory.
   - Search for `.gz` files and extract all into a new directory called `ligand`.

### 4. Install Open Babel

1. **Check Conda Installation:**
   - Ensure Conda is installed. If not, install Miniconda or Anaconda from [here](https://www.anaconda.com/products/distribution).

2. **Create a New Conda Environment:**
   ```sh
   conda create -n myenv python=3.8

3. **Activate the New Environment:**
   ```sh
   conda activate myenv

4. **Add Conda-Forge Channel:**
   ```sh
   conda config --add channels conda-forge

5. **Install Open Babel:**
   ```sh
   conda install openbabel

6. **Verify the Installation:**
   ```sh
   obabel -V

### 5. Use Open Babel 

1. **Combine Ligand Libraries:**
   ```sh
   obabel input1.sdf input2.sdf input3.sdf -O output.sdf

2. **Add Hydrogens:**
   ```sh
   obabel inputfile.sdf -O outputfile.sdf -h

3. **Delete Hydrogens:**
   ```sh
   obabel inputfile.sdf -O outputfile.sdf -d

4. **Convert 1D to 2D Molecules:**
   ```sh
   obabel 1Dstructures.smi -O 2Dstructures.sdf --gen2D

5. **Generate 3D Molecules from 2D:**
   ```sh
   obabel 2Dstructures.sdf -O 3Dstructures.sdf --gen3D

6. **Change File Format from SDF to PDBQT:**
   ```sh
   obabel inputfilename.sdf -O outputfilename.pdbqt

# Blind Docking on AutoDock Vina Using Perl

## Prerequisites

- [MGL Tools](http://mgltools.scripps.edu/)
- [AutoDock Vina](http://vina.scripps.edu/index.html)
- [OpenBabel](https://bit.ly/3eMgXZm)
- [Perl](http://padre.perlide.org/)
- Preprocessed receptor and ligands in PDBQT format

# Installation Steps

### 1. Install AutoDock Vina

1. **Create a dedicated environment for AutoDock Vina:**
   ```sh
   conda create -n vina python=3
   conda activate vina
   conda config --env --add channels conda-forge

2. **Download and build AutoDock Vina:**
    ```sh
    git clone https://github.com/ccsb-scripps/AutoDock-Vina
    cd AutoDock-Vina/build/linux/release
    make

3. **Install the Vina package:**
   ```sh
   cd AutoDock-Vina
   git checkout boost-python
   cd build/python
   python setup.py build install

### 2. Grid Dimension for Blind Docking
    - Ensure the grid box covers the entire molecule.
    - Note the dimensions (x, y, z) and the center of the grid box.

### 3. Install Perl
1. **Download the zipped source code for Unix/Linux:**
    ```sh
    wget https://www.cpan.org/src/5.0/perl-5.28.1.tar.gz

2. **Extract and install Perl:**
   ```sh
   tar -xzf perl-5.28.1.tar.gz
   cd perl-5.28.1
   ./Configure -de
   make
   make test
   make install

3. **Run a Perl script:**
   - Write your Perl script in a text file with a .pl extension.
   - Run the Perl script using:
   ```sh
   perl filename.pl


# Docking Procedure

### 1. Prepare Files
   - Save the Vina_windows.pl script in your current working directory.

### 2. Create a list of all ligands:
    ```sh
    dir /B > Ligand.txt
- Remove any non-ligand PDBQT file names from Ligand.txt.

### 3. Create a configuration file:
    - Make a new text file called conf_vs.txt with the necessary parameters (number of modes, energy range, etc.).

# 2. Run the Docking Script
1. **Ensure all prerequisites are in the same directory:**
   
3. **Execute the Perl script for docking:**
    ```sh
     perl Vina_windows.pl
   
4. **Input the ligand file name when prompted:**
   - Provide Ligand.txt as the input file.
     
5. **Results:**
   - AutoDock Vina results will be saved with the respective ligand root names.

## Conclusion

Follow the steps outlined in this guide to prepare your ligand library efficiently. Make sure to install all necessary software and verify installations before proceeding with Open Babel commands.

Then follow the steps to perform blind docking using AutoDock Vina with a Perl script. Ensure all software and files are correctly installed and configured before running the docking procedure.


   
   
