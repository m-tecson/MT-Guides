# Real Space Refinement with Phenix
The following files are required to run Real Space Refinement on Phenix:
* Your consensus map
  * Note your resolution from CryoSPARC
* Your ISOLDE refined structure from Step 2
* Restraint files for any ligands
  * Some restraint files are available on BOX

  If you do not have restraint files you can generate them through two means. \
  1. Phenix eLBOW
  2. Grade2/Grade Web Server

  Phenix eLBOW utilizes AM1 QM to define ligand restraints which is sufficient for PDB deposition, however, it is not the same algorithm that RCSB/PDB uses. Grade2 utilizes a version of CSD Mogul which aligns with RCSB/PDB parameters and is the recommended version for Phenix RSR and Comprehensive EM Validation runs.

  Grade2 is free and is accessible through https://grade.globalphasing.org/cgi-bin/grade2_server.cgi
  
  