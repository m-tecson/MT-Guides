# Single Structure Refinement and PDB Deposition Guide

### Background: 
This document outlines a general guide on approaching the full PDB deposition pipeline after a cryo-EM map is solved. In the Greene Lab we use 3 primary tools for single structure refinements: Phenix, ISOLDE, and coot.

Phenix (Python-based Hierarchical Environment for Integrated Xtallography) is available freely on SBGrid as well as through an academic license by providing an institutional email address (https://www.phenix-online.org/download)

ISOLDE is a plug-in built into ChimeraX available through the Toolshed and through SBGrid

Coot has multiple distributions including Coot ver 1.x, Coot ver 0.9.x, and Bandicoot ver 0.x. All applications can be used, but Coot ver 0.9.x and Bandicoot ver 1.x are the versions widely used in the Greene Lab. Coot ver 0.9.x is available through SBGrid for both x86 and ARM instruction sets. Bandicoot ver 0.x is available through the Fraser Lab github (https://github.com/fraser-lab/bandicoot/releases). This guide will primarily be using Bandicoot.

Phenix has validation reports available, however, the PDB can be stricter on certain outliers. The RCSB/PDB provides a validation server as well: https://validate-rcsb-4.wwpdb.org/

### Pipeline: 
The typical refinement pipeline would be the following:
Unless an ab-initio reconstruction, you can gather a starting structure from the PDB and align it with your EM map
Run ISOLDE, primarily working on ramachandran plot outliers
Input into Phenix Real Space Refinement
Input in Coot for selective Real Space Refinement and Regularization

Steps 2-4 can be repeated several times until the Molprobity and PDB validation reports are in-line with the underlying chemistry.

Before continuing, it is important to note the following:
1) The symmetry operator applied to your reconstruction
2) The resolution of your reconstruction
3) The quality of your map

The symmetry operator is particularly important as it may speed up refinement if isolated to the asymmetric unit. Furthermore, you can expand symmetry in ChimeraX prior to deposition.

The resolution is important to note as it is an input required for Phenix.

The quality of your map is important as it will determine map-to-model Q-score and whether or not dynamic loops must be deleted. It is necessary to be wary of heterogenous reconstructions as we are unsure of the backbone and sidegroups 'true conformation. A poor quality map with strong structural conclusions will be heavily scrutinized during review.

The current guide was updated and written by Markus on November 4th, 2026\
Current OS: MacOS 27.2 (Golden Gate)

Other OS (Linux-based or Windows) will have similar steps, though certain options may be hidden in different submenus.

