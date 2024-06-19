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
