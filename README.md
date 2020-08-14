# CodeEntropy

CodeEntropy is a python package and a collection of scripts 
that can be used to compute entropy using the multiscale-cell-correlation (MCC) 
theory and force/torque covariance methods. 
The package has can be used to read coordinate and force trajectories from 
two popular MD packages, GROMACS and CHARMM. 

### Installation
Download the git repository and run the following commands.
```
cd dist
tar -xvzf CodeEntropy-XXX.tar.gz
```

`XXX` is the version number of the package. Locate the folder with the file `setup.py`. CD to that folder and type
```
pip install -e .
```

### Usage
The ```CodeEntropy``` python package can be used like as API or via two python scripts which are designed to work with Gromacs and CHARMM files separately. When installing ```codeEntropy``` using the instructions outlined, these scripts are installed as bash executables. Look for
```
mcc_gromacs.py
```
or
```
mcc_charmm.py
```
in the installation directory. By default it is placed in ```/usr/local/bin```. If you do not have administrative priviledges, look for these executables in a user-specific local directory.


##### Fixes and improvments:
In the order best gathered from memory, the following changes have been madeto the code over time through different versions.
1. dihedral double counting is fixed. it solves overestimation of UA-topo entropy. In addition, phi-psi categorization of BB dihedral was introduced.
2. A bug with defining rotational axes system for UA beads using hydrogen-atom position in conjunciton with spherical geometry approach is fixed. This showed that aromatic residues have lower rotational entropy (comparable to expected values for liquids).
3. creation of an exclusive file that contains all the CONSTANTS.
4. Removal of `makemodule.sh` file.
5. Can read CHARMM topology and trajectory (coordinate/forces) and a separate executable for charmm inputs is now available.
6. TOPO method 2 does both SC and BB entropy calculation, but separately.
7. Minor changes to DCD reading code.
8. Minor bugs related to CHARMMREADER/PSFREADER fixed.
9. CHARMMREADER unit conversion fixed and UnitsAndConversions module modified.
10. Minor bug fix in the Gromacs Reader section.
11. Adaptive Enumeration Method (AEM) of computing topographical entropy is introduced. With it some data structures have also been introduced.
12. Printing FF/TT Matrices by default to a file with a fixed name is removed and a control is established via ```--mout <filename>``` flag.
13. Printing NMD format files by default to a set of files, with hierarchy-level dependent names, is removed and a control is established via ```--nmd <filename>``` flag. 
14. Function returning principal axes matrix is modified to return it such that the axes are in the rows and not in the columns to reconcile with the 4x3 format for coordinate axes used in the rest of the program.
