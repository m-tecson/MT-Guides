# PDB Depositions through OneDep
This step discusses the deposition process using OneDep and PDB Extract. Here are some files that are necessary for the deposition process:
1. Your consensus map
2. Your half maps (half map A and half map B) for GSFSC calculations
3. The FSC mask calculated by CryoSPARC for GSFSC calculations
4. The GSFSC curve as .xml from CryoSPARC
5. A picture of the map (this can be taken from ChimeraX)
6. Your solved structure

Total files: 7 (2 half maps)

For your maps and masks note the following:
* Pixel size (dependent on collection, available on CryoSPARC and in the ```.mrc``` header)
* Contour (available in ChimeraX)
  * Contour for FSC mask is always 1

In addition to those 7 files, it is recommended to also have an ORCID to easily access all depositions and share it with all other authors. To create an ORCID visit [orcid.org](https://orcid.org/)

After ensuring you have all files and your ORCID, discuss with Dr. Greene or your team the deposition strategy. Many cryo-EM data collections will have similar settings so you can import most fields from an initial or previous deposition session. Additionally, you may gather cryo-EM  collection metadata from an deposited ```.cif``` file using [PDB extract](https://pdb-extract.wwpdb.org/) Option A.

If you have a master metadata file, it is recommended to combine your final structure from the previous step using [PDB extract](https://pdb-extract.wwpdb.org/) Option B. Additionally, Option B is particularly useful for repairing and converting broken ```.pdb``` files to the ```.cif``` format for deposition.