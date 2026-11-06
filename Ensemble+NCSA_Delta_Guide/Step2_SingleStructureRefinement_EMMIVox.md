# Single Structure Refinement on EMMIVox
Single Structure Refinement is a prerequisite for ensemble generation and modeling. Similar to ISOLDE, EMMIVox utilizes molecular dynamics simulations to minimize and and refine structures with cryo-EM maps as a restraint, similar to Real-space refinement.

Some file management is crucial before running EMMIVox. Depending on approach, you may set up directories locally on your laptop then use `rsync`, `scp`, or Globus to transfer the parent project directory.

You may also set up directories on NCSA Delta, however, consistency depends on server load and Proxy ID errors are frequent requiring a lot of patience.

Below is a tree of the file structure:
```
project_name (ex. WT_hGS_turnover_C1)
├── 1-refinement
│   ├── 0-Building
│   ├── 1-Map-Preparation
│   ├── 2-Equilibration
│   ├── 3-Map-Scaling
│   ├── 4-Production
│   └── 5-Analysis (NOT REQUIRED)
└── 2-ensemble
    ├── 0-Production
    └── 1-Analysis (REQUIRED)
```

You may also find an example directory [here](/Ensemble+NCSA_Delta_Guide/WT_hGS_turnover_C1_SAMPLE/)\
In these directories, you will also find sample `.slurm` scripts to queue jobs on NCSA Delta as well as other text and data files necessary to run each step.

This guide won't be as detailed as the EMMIVox tutorial written [here](https://github.com/COSBlab/EMMIVox/tree/main/tutorials/1-refinement)

## Data Import
As previously described, there are three ways to import data:
1) `rsync`
2) `scp`
2) Globus

`rsync` and `scp` is ideal for smaller data transfers while Globus is recommended for large data transfers. 

[NCSA Delta documentation](https://docs.ncsa.illinois.edu/systems/delta/en/latest/user_guide/data_mgmt.html#transferring-data) describes `rsync` and `scp` here as well as a more detailed guide on utilizing Globus for large file transfer.

Visit the [Globus website](https://www.globus.org/) for more information. If you are creating an account with Globus, utilize your institutional email.

## Initializing the Environment
Certain Python dependencies are required for EMMIVox scripts, to ensure that all scripts successfully run we need to establish a specific build of conda.

Access a login node using the [Delta OnDemand terminal or SSH](https://docs.ncsa.illinois.edu/systems/delta/en/latest/user_guide/login.html#ssh-keyboard-interactive). Once you have successfully logged into compute resources, run:\
`/sw/external/python/miniforge3-pytorch-2.7.0/bin/conda init bash`\
This will add this specific build of conda to your `~/.bashrc`. After running, either refresh your terminal window if accessed through Delta OnDemand or run `source ~/.bashrc` to refresh your session.

Next, we will install necessary dependencies by running:\
`pip install MDAnalysis==2.7.0 scipy==1.18.0 mrcfile biopython`

After running these commands, you may proceed to processing your data.

## Notes on running sbatch jobs on NCSA Delta
Total time to complete each task will depend on the system size and what atoms/subunits are defined during these steps. It is a good rule of thumb to use `.slurm` scripts and `sbatch` over terminal to queue jobs. All slurm scripts are adapted from the EMMIVox guide.

It's recommended to write `.slurm` scripts before doing any processing, example scripts are provided in the [sample directory](/Ensemble+NCSA_Delta_Guide/WT_hGS_turnover_C1_SAMPLE/). After writing `.slurm` scripts, import them to their respective 'step directory' (e.g. project_directory/1-refinement/0-Building).

To run a job using sbatch, first navigate to the particular 'step directory' by running: `cd project_directory/1-refinement/0-Building`.

Then run `sbatch 0-building.slurm`, this will send the job to the scheduler. You will be notified via email when the job hits a compute node, if it fails, or if it successfully completes. The scheduler will also provide you a `jobid`. Keep note of this number as it is crucial for queuing back to back jobs. If you forgot you may also run `squeue -u $user` to see what jobs you have queued.

You do not need to wait for each job to finish. You can also queue jobs back to back by adding the `--dependency=afterok:[jobid]` flag. This flag tells the scheduler, only run this script if the previous job ran successfully.

For example:
```
(base) [mtecson@dt-login01 0-Building]$ sbatch 0-building.slurm
Submitted batch job 2337924
(base) [mtecson@dt-login01 0-Building]$ cd ../1-Map-Preparation
(base) [mtecson@dt-login01 1-Map-Preparation]$ sbatch 1-map-prep.slurm --dependency=afterok:2337924
```

The 1-map-prep.slurm script won't run unless the previous 0-building job successfully completes.
