# CodeEntropy

CodeEntropy is a python package and a collection of scripts 
that can be used to compute entropy using the multiscale-cell-correlation (MCC) 
theory and force/torque covariance methods. 
The package can be used to read coordinate and force trajectories from 
two popular MD packages, GROMACS and CHARMM. 

### Contact
Any questions regarding the code and its usage can be emailed to:
Arghya Chakravorty, PhD (arghyac@umich.edu)  \
Richard Henchman, PhD (rhen7213@uni.sydney.edu.au)

### Latest Stable Version
Version 0.4 (DATE ???)

### Installation
We recommend downloading the latest version of the code. 
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
The ```CodeEntropy``` python package can be used like as API or via two python scripts which are designed to work with Gromacs and CHARMM files separately. When installing ```CodeEntropy``` using the instructions outlined, these scripts are installed as bash executables. Look for
```
mcc_gromacs.py
```
or
```
mcc_charmm.py
```
in the installation directory. By default it is placed in ```/usr/local/bin```. If you do not have administrative priviledges, look for these executables in a user-specific local directory.

To run MCC entropy calculations using the `mcc_gromacs.py` executable, type
```
mcc_gromacs.py 
```
or 
```
mcc_gromacs.py --help
```
to print the help message.

To use CHARMM generated DCD and PSF files, you will need to use the `mcc_charmm.py` executable. Accordingly type `mcc_charmm.py` or `mcc_charmm.py --help` to print the help message.

## Citation
If this code is used to publish a work, please cite:
Chakravorty A, Higham J, Henchman R, **Entropy of proteins using Multiscale Cell Correlation**, *J. Chem. Inf. Model.* 2020
DOI: doi.org/10.1021/acs.jcim.0c00611


### Fixes and improvments:
In the order best gathered from memory, the following changes have been made to the code over time through different versions. Most recent change is at the bottom of this list and is included in the latest available version.

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
15. Minor bug fix in Trajectory.PSFReader and improvement in printing HELP message when no input flag is provided in the command line following the executables.
16. Minor change in verbosity of print statements in DCDReader.
17. Atomselection features have been added. Entropy functions now use 'atomselection' features to define cells/beads. Some vestigial functions in `BaseMolecule` class have been removed. A complaint, that kills the run is added when gromacs TRR file is found to contain no force.
18. New atomselection tokens added. Entropy functions cleaned up and optimized.
19. Custom exceptions and clean-ups added for better error handling.
20. Time and duration printing feature added.
21. BaseMolecule also stores segment information now. Readers updated accordingly and additional changes have been made. Selection feature expanded, can use SEGI/SEGN (select by segment), BYREsidue, BYSEgid, RESDue now. New selection keywords (like seen in CHARMM) are added. 
22. v0.3: (a) PSFReader has been expanded and a new function to write a PSF has been added. (b)  Atomselection by  SUBSET is now possible and some bugs in selection functions have been fixed. (c) A bug in DCDreader's timestamping has been fixed (d) Minor bug fixes to AtomSelection.
23. v0.4: Some minor changes to CustomFunctions.py file
____________

