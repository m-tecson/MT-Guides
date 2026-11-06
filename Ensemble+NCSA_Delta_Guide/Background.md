# Single Structure Refinement and Ensemble Modeling Utilizing EMMIVox on NCSA Delta
The following folder will walk you through a step-by-step guide on utilizing [EMMIVox](https://github.com/COSBlab/EMMIVox) to understand the conformational heterogeneity of our cryo-EM maps. 

The general workflow of Ensemble Modeling utilizing EMMIVox is as follows:
1. Solvation and neutralization utilizing [CHARMM-GUI](https://www.charmm-gui.org/)
2. Single Structure Refinment utilizing EMMIVox on NCSA Delta
3. Ensemble Modeling utilizing EMMIVox on NCSA Delta

Step 1 requires your satisfactory structure (`.pdb` legacy-format preferred)\
Step 2 requires inputs from CHARMM-GUI, your consensus map, half maps A and B, and your satisfactory structure from step 1\
Step 3 requires data from step 2

Discuss approach with the PI and create an account with your institutional email before proceeding.

Software versions as of 11/05/2026:
PLUMED-2.10.0\
GROMACS-2022.5