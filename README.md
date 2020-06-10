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

##### Fixes and improvments:
In the order best gathered from memory, the following changes have been madeto the code over time through different versions.
1. dihedral double counting is fixed. it solves overestimation of UA-topo entropy. In addition, phi-psi categorization of BB dihedral was introduced.
2. A bug with defining rotational axes system for UA beads using hydrogen-atom position in conjunciton with spherical geometry approach is fixed. This showed that aromatic residues have lower rotational entropy (comparable to expected values for liquids).
3. creation of an exclusive file that contains all the CONSTANTS.
4. Removal of `makemodule.sh` file.
5. Can read CHARMM topology and trajectory (coordinate/forces) and a separate executable for charmm inputs is now available.
