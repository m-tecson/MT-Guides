# Single Structure Refinement on EMMIVox
Single Structure Refinement is a prerequisite for ensemble generation and modeling. Similar to ISOLDE, EMMIVox utilizes molecular dynamics simulations to minimize and and refine structures with cryo-EM maps as a restraint, similar to Real-space refinement.

Some file management is crucial before running EMMIVox. Depending on approach, you may set up directories locally on your laptop then use SSH or Globus to transfer the parent project directory.

You may also set up directories on NCSA Delta, however, consistency depends on server load and Proxy ID errors are frequent requiring a lot of patience.

Below is a tree of the file structure:\
```
project_name (ex. WT_hGS_turnover_C1)
├── 1-refinement
├── 0-building
│   ├── 1-map-preparation
│   ├── 2-equilibration
│   ├── 3-map-scaling
│   ├── 4-production
│   └── 5-analysis (NOT REQUIRED)
└── 2-ensemble
    ├── 0-production
    └── 1-analysis (REQUIRED)
```

You may also find an example directory [here](/Ensemble+NCSA_Delta_Guide/WT_hGS_turnover_C1_SAMPLE/)\
In these directories, you will also find sample `.slurm` scripts to queue jobs on NCSA Delta as well as other text and data files necessary to run each step.

This guide won't be as detailed as the EMMIVox tutorial written [here](https://github.com/COSBlab/EMMIVox/tree/main/tutorials/1-refinement)

